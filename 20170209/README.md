## 20170209#

#### 스택
* 지역변수와 매개변수를 저장
* 메소드가 종료되면 삭제됨
* 가변적으로 계속 만들어지고 사라지는 것들이 들어감…Ex. 클래스 안에서만 생성되어 사용되는 프로퍼티
* Last In First Out
* 자료를 1,2,3 번 식으로 이름을 정해서 넣고 맨 마지막에 들어온 자료부터 빼내는 식

> ex. 뒤로가기 버튼을 누르면 가장 마지막 홈피 이전 페이지 부터 역순으로 뜨는 것

> ex. 설정 <-- 와이파이 <-- 와이파이 고르는 창

* 이들 데이터는 내부적으로 리스트로 연결되어 있을 확률이 높음
* 자료 쌓기는 푸쉬, 자료 꺼내기는 팝으로 명칭

#### 큐 
* First In First Out 
* "큐는 작업대기열, 여럿이 서있는 줄을 의미함"
* 작업대기열에서 가장 많이 사용함

> CPU 스케줄링


> 디스패치 큐

* 자료 넣기는 풋, 자료 꺼내기는 겟으로 명칭

#### 덱
* 스택과 큐의 합. 스택과 큐를 활용하기에 애매한 경우에 스택과 큐를 합침
* 순차적으로 쌓인 자료들 앞에서도, 뒤에서도 데이터를 빼오는 것이 가능
* 단 쌓인 자료의 중간을 빼오기는 불가능
* Double Ended Queue 라고도 명칭함

#### 힙
* 동적 할당을 위한 영역(객체)
* heap의 사이즈는 매우 유동적이며, 해당 공간에 들어가는 데이터들도 매우 유동적임…해당 공간에 들어가는 데이터의 예시가 바로 객체임    

#### 데이터
* 전역변수와 정적변수(Static이라는 코드 사용하여 지정)를 저장
* 프로그램이 종료될 때까지 저장됨

#### 코드 
* 프로그램의 코드 저장
* 메소드 코드가 코드영역제 저장되는 예시임
* 프로그램이 종료될 때까지 저장   

> 메모리 영역의 예시

		NSInteger a = 4;
		NSInteger b;     
		//이들 코드는 어떻게 들어갈까?     

> * a = 4 , b 는 스택으로.   
NSInteger는 코드로 들어감


## 정렬알고리즘

**“개발자의 기본소양” “힙정렬까지는 어떻게 돌아가는지 알아야 함” “ios개발자에게 가장 많이 묻는 것이 GCD, 정렬알고리즘의 이해, 스택 큐”**

### 정렬알고리즘의 효율
* 비교연산의 횟수와 이동연산의 횟수를 통해 효율을 측정
* 단순 비효율 정렬 :  삽입정렬, 선택정렬, 버블정렬
* 복잡 효율 정렬 : 합병정렬, 퀵 정렬, 힙 정렬, 기수 정렬

### 알고리즘복잡도
* 가장 최악의 경우에 걸리는 시간…시간은 비교연산의 횟수와 이동연산의 횟수를 통해 산출
* Big O 표기법으로 표기…O(n)…”n번 검사, 비교하면 원하는 데이터를 찾을 수 있다”, O(n logn)…”10000번이라고 가정하고, 40000의 시간동안 검사, 비교하면 원하는 데이터를 찾을 수 있다.
* small o…”최선의 경우일 때 데이터 검사시 걸리는 시간”


### 단순 비효율 정렬 알고리즘 종류

#### 선택정렬
* 가장 쉬운 정렬방법
* 모든 데이터를 읽고, 리스트의 데이터중 가장 작은 데이터 순으로 앞쪽에 정렬하는 방식…다시 모든 데이터 읽기, 정렬하기의 반복
* 최선:O(n2) 평균:O(n2) 최악:O(n2)

#### 삽입정렬
* 데이터의 비교에 따라 적절한 자리에 삽입하는 방식
* 손안의 카드를 정렬시키는 것과 같은 방법
* 데이터들을 읽으면서, 원하는 위치를 찾는 것
* 최선:O(n) 평균:O(n2) 최악:O(n2)

#### 버블정렬
* 인접한 데이터와 비교하여 정렬
* 리스트의 왼쪽에서 오른쪽까지 한번 비교, 교환 과정이 완료되면, 가장 큰 수가 오른쪽 끝으로 이동함
* 모든 숫자가 정렬될 때 까지 실행
* 최선:O(n2) 평균:O(n2) 최악:O(n2)

### 복잡 효율 정렬 알고리즘   
* Divide and Conquer Algorithms
* “문제를 해결이 가능한 정도까지 쪼갠다”.   
* “해결한 다음에 문제들을 다시 합친다”.   
* “다시 합치면 해결이 가능할 정도로 쉬운 문제가 되거나 해결되어 있다”.   
* 보통 재귀함수를 통해 자연스럽게 구현한다.   

> 재귀함수의 특징 : CPU에 매우 많은 부하를 준다

#### Quick Sort   
* 기준점(피벗)을 만들어 왼쪽과 오른쪽으로 분류한다
* 분류가 끝나면 다시 병합한다
* O(log2n) 평균:O(log2n) 최악:O(n2)

#### Merge Sort
* 리스트의 길이를 0으로 나눈다
* 나누고 병합할때 비교를 하며 병합한다
* 최선:O(log2n) 평균:O(log2n) 최악:O(log2n)