# Emplace
C++의 STL에서 제공해주는 함수로 컨테이너에서 키값으로 된 요소가 없을 때 새로운 요소를 삽입 시켜주는 함수

emplace를 사용하면 불필요한 복사 또는 이동작업을 피하면서 요수를 추가할 수 있음

    vector나 queue에 넣을 때 여러 인자로 pair나 tuple을 만들 필요없이 바로 넣을수 있게 해주기 때문에 불필요한 복사난 이동이 없음

반복자 및 참조자가 무효화 되지않음

# Vector
배열처럼 순차적으로 데이터를 저장하는 시퀀스 컨테이너로 쉽게 말해서 가변 배열이라고 할 수 있음

순차적으로 데이터가 저장되어있기 때문에 접근하는 것이 매우 빠름
- 임의의 위치를 탐색할 때 O(1)
- 임의의 위치에 데이터를 삽입 삭제 O(n)

벡터는 일반적으로 원소의 개수보다 더 많은 공간이 할당되어 있음

할당 되어있는 공간을 모두 사용했을 경우 새로운 공간에 더 큰 공간을 할당해서 데이터들을 복사해서 옮김

반복자를 이용해서 접근이 가능함
- 컨테이너 원소에 접근할수 있는 포인터와 같은 객체

하지만 데이터를 삽입 삭제하면 반복자가 무효화되어 사용할 수 없음 반복자를 다시 갱신해서 사용해야 함

# List
양반향 연결구조를 가진 자료형

Vector와 달리 임의의 위치에 바로 접근할 수 없음 시작위치와 마지막위치만 기억하고 있기 때문에 임의의 위치에 접근하고 싶다면 연결된 부분을 타고 들어가야함

리스트는 벡터와 다르게 임의의 위치에 데이터를 삽입하는 것이 매우 빠름 연결 부분만 갈아 치우면 되기 때문

리스트는 벡터와 다르게 삽입 삭제 작업을 해도 반복자가 무효화되지 않음
