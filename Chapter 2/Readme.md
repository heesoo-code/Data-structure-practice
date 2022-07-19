파이썬과 함께하는 자료구조의 이해 공부 Ch2
=============

1. 단순연결리스트
------

**단순연결리스트(Singly Linked List)** 는 동적 메모리 할당을 이용해 노드들을 한 방향으로 연결하여 리스트를 구현하는 자료구조.

![Alt text](/Chapter%202/%EC%98%88%EC%8B%9C.png)

**단순연결리스트** 에서는 삽입이나 삭제시 항목들이 땡겨지거나 옮길필요가 없다. 하지만 원하는 항목을 탐색하려면 무조건 첫 노드부터 탐색해야 하기 때문에 **순차탐색(Sequential Search)** 을 해야만 한다.

<pre>
<code>
<python>
class SList:
    class Node
        def __init__(self, item, link):
            self.item = item    // 노드 생성자
            self.next = link   // 다음 노드 레퍼런스
    
    def __init__(self):
        self.head = None   // 단순연결리스트 생성자, head와 항목 수(size)로 구성
        self.size = 0

    def size(self): return self.size
    def is_empty(self): return self.size == 0

    def insert_front(self, item):
        if self.is_empty():   // empty일경우에
            self.head = self.Node(item, None)   // head가 새 노드 참조
        else:
            self.head = self.Node(item, self.head)    // head가 새 노드 참조
        self.size += 1
    
    def insert_after(self, item, p):
        p.next = SList.Node(item, p.next)   // 새 노드가 p 다음 노드가 됨
        self.size += 1
    
    def delete_front(self):
        if self.is_empty():   // empty인 경우 에러처리
            raise EmptyError('Underflow')
        else:
            self.head = self.head.next   // head가 둘쨰 노드를 참조
            self.size -= 1

    def delete_after(self, p):
        if self.is_empty():   // empty인 경우 에러처리
            raise EmptyError('Underflow')
        t = p.next
        p.next = t.next   // p 다음 노드를 건너뛰어 연결
        self.size -= 1

    def search(self, target):
        p = self.head   // head부터 순차탐색
        for k in range(self.size):
            if target == p.item: return k    // 탐색 성공의 경우
            p = p.next
        return None    // 탐색 실패일 경우

    def print_list
        p = self.head
        while p:
            if p.next != None:
                print(p.item, ' -> ', end='')
            else:
                print(p.item)
            p = p.next    // 노드들을 순차 탐색

class EmptyError(Exception):
    pass
</python>
</code>
</pre>


삭제 연산 수행시 연결리스트가 empty일 경우 **Underflow** 가 발생한다.

------
2.이중연결리스트
------

**이중연결리스트(DOubly Linked List)** 는 각 노드가 두 개의 레퍼런스를 가지고 각각 이전 노드와 다음 노드를 가리키는 연결리스트이다.

![Alt text](/Chapter%202/%EC%98%88%EC%8B%9C2.png)



------
3.원형연결리스트
------

**원형연결리스트(Circular Linked List)** 는 마지막 노드가 첫 노드와 연결된 단순연결리스트이다.

![Alt text](/Chapter%202/%EC%98%88%EC%8B%9C3.png)

- 점근표기법
수행시간은 알고리즘이 수행하는 기본 연산 횟수를 입력 크기에 대한 함수로 표현한 것이다. 이러한 함수는 주로 여러 개의 항을 가지는 다항식으로 표현되므로 이를 입력의 크기에 대한 함수로 표현하기 위해 점근표기법이 사용된다.

- 3가지의 대표적인 점근표기법(추가이해 필요)
1. O (Big-Oh)-표기법

    모든 N ≥ N<sub>0</sub>에 대해서 f(N) ≤ cg(N)이 성립하는 양의 상수 o와 N<sub>0</sub>이 존재하면, f(N) = O(g(N))이다. 점근적 상한만 알고 있을때 사용하는 표기법이다.

2. Ω (Big-Omega)-표기법

    모든 N ≥ N<sub>0</sub>에 대해서 f(N) ≥ cg(N)이 성립하는 양의 상수 c와 N<sub>0</sub>이 존재하면, f(N) = Ω(g(N))이다. 점근적 하한만 알고 있을떄 사용하는 표기법이다.

3. Θ (Theta)-표기법

    모든 N ≥ N<sub>0</sub>에 대해서 c<sub>1</sub>g(N) ≥ f(N) ≥ c<sub>2</sub>g(N)이 성립하는 양의 상수 c<sub>1</sub>, c<sub>2</sub>, N<sub>0</sub>이 존재하면, f(N) = Θ(g(N))이다. 상한과 하한을 둘다 알고 있을때 사용하는 표기법이다.

------
4.파이썬 언어에 대한 기본적인 지식
------

파이썬은 객체지향 프로그래밍 언어로 **클래스(Class)** 를 선언하여 객체에 데이터를 저장하고 **메소드(Method)** 를 선언하여 객체들에 대한 연산을 구현한다.

파이썬에서 **인스턴스 변수(Instance Variable)** 는 객체에 정보를 저장하기 위해 선언한다.
객체를 생성하기 위한 **객체 생성자(Constructor)** 를 클래스 내부에 선언한다.

<pre>
<code>
class Student:
    def _init_(self, name, id) //student의 객체 생성자
        self.name = name //인스턴스 변수
        self.id = id //인스턴스 변수
    def get_name(self):      //name을 리턴하는 메서드
        return self.name
    def get_id(self):        //id를 리턴하는 메서드
        return self.id

</code>
</pre>

파이썬의 리스트는 동적 배열의 개념으로 구현되어 있어서 프로그램이 수행되는 도중에 리스트에 항목이 추가되거나 삭제되면 즉시 리스트를 확장화거나 축소한다.

조건문 if-esle
반복문 for

내장함수
- ord('문자') 문자의 unicode값을 리턴
- list(reversed(리스트)) 역순으로 된 리스트를 리턴한다
- 리스트.reverse() 리스트를 역순으로 만든다

lambda 함수는 함수의 이름도 return도 없이 수행되는 함수

------
5.순환
------

**순환(Recursion)** 은 함수의 실행 과정 중 스스로를 호출하는 것이다. 다만 호출하다보면 무한히 호출하는 경우가 발생할 수 있어 count 매개변수를 전달하여 count가 0에 도달하면 멈추도록 제어할 수 있다.

순환이 함수의 마지막 부분에서 이뤄질 경우 이를 **꼬리 순환(Tail Recursion)** 이라고 하며 이와 같은 방식이 수행 속도와 메모리 사용 측면에서 효율적이다.


------
연습문제
------
1.1
a)자료구조
b)시간, 공간
C)기본 연산 횟수, 함수

1.2
1

1.3
2



ㅇㅇㅇㅇㅇㅇㅇㅇㅇㅇㅇㅇ