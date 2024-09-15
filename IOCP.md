# IOCP ( Input/Output Completion Port )
I/O 처리를 비동기 방식으로 처리하는 방법
비동기(Asynchronous) + 스레드 풀링(Thread Pooling) + 논 블로킹(Non-Blocking) + 중첩 입출력(Overlapped I/O)과 같은 개념들을 이용

- 비 동기
    - 독립적으로 진행되는 작업
    - 병렬 처리를 진행 쓰레드를 사용한다는 뜻


- 여기서의 I/O 처리는 주로 소켓이나 파일 입출력을 말함

- IOCP는 커널 오브젝트임
