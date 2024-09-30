# IOCP ( Input/Output Completion Port )
I/O 처리를 비동기 방식으로 처리하는 방법
비동기(Asynchronous) + 스레드 풀링(Thread Pooling) + 논 블로킹(Non-Blocking) + 중첩 입출력(Overlapped I/O)과 같은 개념들을 이용

- 비 동기
    - 독립적으로 진행되는 작업
    - 병렬 처리를 진행 쓰레드를 사용한다는 뜻


- 여기서의 I/O 처리는 주로 소켓이나 파일 입출력을 말함

- IOCP는 커널 오브젝트임

## 전체적인 처리 과정
1. 비동기 I/O 작업 요청
    - 우선 I/O에 대한 처리를 비동기적으로 처리
    - 입출력과정은 매우 오래 걸리는 작업이기 때문에 입출력 작업을 비동기 적으로 실행

2. I/O작업 완료 통지
    - 처리가 완료된 것들을 queue형태로 된 완료포트에 담아 둠
    - 이 때까지 프로그램은 I/O작업완료까지 대기하지 않고 다른 작업을 수행

3. 쓰레드를 풀을 통한 결과 처리
    - 쓰레드 풀의 쓰레드가 완료포트에서 대기하다가 완료된 작업의 결과를 가져와서 처리
        - I/O작업에 대한 결과를 가져옴, 이후 필요한 후처리를 진행함

## Overlapped IO
Non-blacking 모드로 동작하며 비동기적으로 I/O를 제어하기위한 I/O 처리방법

기본적인 I/O작업은 동기로 이루어짐 (Blocking 모드)
- ReadFile함수 호출시 읽기 작업이 끝나기 전까지 함수는 값을 반환하지 않고 처리를 기다림
    - 동기적으로 I/O를 처리
    - 작업이 끝날 때 까지 다른 작업을 수행하지 못하고 대기해야하는 상태를 Blocking모드라고 함

Non-Blocking모드는 I/O작업을 호출하고 바로 반환함
- 스레드는 I/O작업을 대기하지 않고 다른 작업을 수행할 수 있음

Overlapped IO 동작 방식
1. 작업을 요청
2. WSASend함수를 호출( 데이터를 전송하는 역할,Overlapped IO구조체를 파라미터로 전달 )
3. 비동기적으로,I/O작업을 요청했다는 정보를 Device Driver에게 전송
    - 전송을 완료한 쓰레드는 더이상 I/O작업을 신경쓰지 않음
4. Device Driver에서 I/O작업을 주시하다가 끝나면 끝났음을 알려줌
5. 이후 완료 여부를 확인
    - Overlapped 구조체에 이벤트 커널 오브젝트를 등록-> 이벤트 객체를 singaled 상태로 변경해서 완료여부를 확인함
    - WSAGetOverlappedResult함수를 호출하면서 IO의 완료및결과를 확인

- 이 방식은 IO를 요청한 쓰레드에서 처리하는 방법으로 해당 쓰레드가 작업이 완료되었는지 계속확인해야함

IOCP방식

1. 완료포트 생성 ( CP,Completion Port )
    - 완료포트는 IO작업의 완료 알림을 받을 수 있는 커널 오브젝트임
2. IO객체와 CP객체연결
    - CreationIOPort함수를 사용해서 해당 IO객체를 CP와 연결
    - 연결되면 완료알림을 받을 수 있음
        - 커널레벨에서 작업이완료되면 CP객체에 자동으로 전달함
3. 비동기 IO 작업의 시작
    - IO작업이 완료되면 해당 작업에 대한 결과와 함께 CP객체로 알림이 옴
    - 이때 중요한 것은 Overlaped구조체를 넘김
        - 작업의 상태를 기록하고 추적하는 역할을 함
4. 작업자 스레드 생성
    - 일반적으로는 스레드 풀을 사용
    - 작업자 스레드는 CP에서 알림을 받아 IO작업을 처리
5. 작업자 스레드 대기
    작업자 스레드는 CP에서 알림을 기다림

6. IO작업 완료 알림 처리
    - IO작업이 완료되면 해당 작업의 결과와 함께 완료포트로 알림이 전달됨
    - 작업자 스레드는 이 알림을 받아 작업을 처리하고 필요에 따라 추가 작업을 수행

요약

소켓이나 파일을 읽어드리면 스레드에서 비동기IO작업을 운영체제에 요청하고 다른작업을 하러감
    - 논 블록킹 방식을 이용 쓰레드를 계속해서 이용하기 때문에 컨텍스트 스위칭이 적게 일어남

요청할 때 IO객체와 CP객체를 연결하고 Overlapped 구조체를 생성해서 같이 넘겨줌
    - Overlapped 구조체는 작업의 상태를 기록하고 추적함
    - Overlapped 구조체가 있어야 알림을 받을 수있음 ( IO작업당 하나씩 생성 )
    - CP객체는 1개이고 IO객체는 여러개로 1:N의 형태로 연결됨

이후 IO작업이 완료되면 CP객체에 완료알림을 보냄

CP에서 알림을 받으면 CP내의 큐에 완료된 작업을 넣어 놓음

쓰레드 풀에서 대기중인 쓰레드를 할당해서 후처리를 진행하게됨

IOCP서버는 비동기IO작업이 소켓의 네트워크 통신 작업이 추가된것임