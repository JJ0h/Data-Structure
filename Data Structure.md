# 1. LeetCode 225. Implement Stack using Queues

```python
class MyQueue:
    def __init__(self):
        self.stack_in = []
        self.stack_out = []

    def push(self, x: int) -> None:
        self.stack_in.append(x)

    def pop(self) -> int:
        self.move()
        return self.stack_out.pop()

    def peek(self) -> int:
        self.move()
        return self.stack_out[-1]

    def empty(self) -> bool:
        return not self.stack_in and not self.stack_out

    def move(self):
        if not self.stack_out:
            while self.stack_in:
                self.stack_out.append(self.stack_in.pop())
```

# 2. LeetCode 232. Implement Queue using Stacks

```python
class MyQueue:
    def __init__(self):
        self.stack_in = []
        self.stack_out = []

    def push(self, x: int) -> None:
        self.stack_in.append(x)

    def pop(self) -> int:
        self.move()
        return self.stack_out.pop()

    def peek(self) -> int:
        self.move()
        return self.stack_out[-1]

    def empty(self) -> bool:
        return not self.stack_in and not self.stack_out

    def move(self):
        if not self.stack_out:
            while self.stack_in:
                self.stack_out.append(self.stack_in.pop())
```

# 3. 교재의 큐 연습문제

```python
class Queue:
    def __init__(self):
        self.__queue = []

    def enqueue(self,x):
        self.__queue.append(x)

    def dequeue(self):
        return self.__queue.pop(0)

    def front(self):
        return self.__queue[0]

    def isEmpty(self) -> bool:
        return len(self.__queue)==0

    def dequeueAll(self):
        self.__queue.clear()

    def __len__(self):
        return len(self.__queue)

    def printQueue(self):
        print("Queue from front:", end='')
        for i in range(len(self.__queue)):
            print(self.__queue[i],end='')
        print()


# 3. 1.
class ListQueue:
    def __init__(self):
        self.__queue = []

    def enqueue(self,x):
        self.__queue.insert(0,x)

    def dequeue(self):
        return self.__queue.pop()

    def front(self):
        return self.__queue[-1]

    def isEmpty(self) -> bool :
        return len(self.__queue) == 0

    def dequeueAll(self):
        self.__queue.clear()
        
        
# 3. 2.
def is_str_wsw():
    CheckQ = Queue()
    k = input("문자를 입력하시오: ")

    mid = k.find('$')
    if mid == -1:
        return False

    for i in range(mid):
        CheckQ.enqueue(k[i])

    for i in range(mid + 1, len(k)):
        if CheckQ.isEmpty():
            return False
        m = CheckQ.dequeue()
        if m != k[i]:
            return False

    return CheckQ.isEmpty()


# 3. 3.
from DS.list.circularLinkedList import CircularLinkedList

class LinkedQueue:
    def __init__(self):
        self.__queue = CircularLinkedList()

    def enqueue(self, x):
        self.__queue.append(x)

    def dequeue(self):
        return self.__queue.pop(0)

    def front(self):
        return self.__queue.get(0)

    def isEmpty(self) -> bool:
        return self.__queue.isEmpty()

    def dequeueAll(self):
        self.__queue.clear()

    def __len__(self):
        return len(self.__queue)

QueueA = LinkedQueue()
QueueB = LinkedQueue()

def CopyQ_A_to_B():
    for i in range(len(QueueA)):
        k = QueueA.dequeue()
        QueueA.enqueue(k)
        QueueB.enqueue(k)


# 3. 4.
class StackFromQueue:
    def __init__(self):
        self.__StackFQ = []
        self.SFQueueA = Queue()
        self.SFQueueB = Queue()

    def push(self,x):
        self.SFQueueA.enqueue(x)

    def pop(self):
        for i in range ((len(SFQueueA))-1):
            k = self.SFQueueA.dequeue()
            self.SFQueueB.enqueue(k)
        k = self.SFQueueA.dequeue()
        self.SFQueueA, self.SFQueueB = self.SFQueueB, self.SFQueueA
        return k


# 3. 5.
class Stack:
    def __init__(self):
        self.__stack = []

    def push(self, x):
        self.__stack.append(x)

    def pop(self):
        return self.__stack.pop()

    def __len__(self):
        return len(self.__stack)

class QueueFromStack:
    def __init__(self):
        self.__QueueFS = []
        self.QFStackA = Stack()
        self.QFStackB = Stack()

    def enqueue(self,x):
        self.QFStackA.push(x)

    def dequeue(self):
        for i in range((len(self.QFStackA))-1):
            k = self.QFStackA.pop()
            self.QFStackB.push(k)
        f = self.QFStackA.pop()
        self.QFStackA, self.QFStackB = self.QFStackB, self.QFStackA
        return f


# 3. 6.
# 두 알고리즘 모두 Θ(n) 의 수행시간이 걸릴 것이다.


# 3. 7.
# 두 알고리즘 모두 큐의 사이즈 n에 비례하여 O(nlongn)의 시간이 걸릴 것으로 추정된다.


# 3. 8.
class ListQueue:
    def __init__(self):
        self.__queue = []

    def enqueue(self, x):
        self.__queue.append(x)

    def dequeue(self):
        return self.__queue.pop(0)

    def front(self):
        if self.isEmpty():
            return None
        else:
            return self.__queue[0]

    def isEmpty(self) -> bool:
        return (len(self.__queue) == 0)

    def dequeueAll(self):
        self.__queue.clear()

    def printQueue(self):
        print("Queue from front:", end=' ')
        for i in range(len(self.__queue)):
            print(self.__queue[i], end=' ')
        print()

    def Deque(self,c,x,y):
        if c == 'from front' :
            if x == 'en':
                self.__queue.insert(0,y)
            elif x == 'de' :
                self.dequeue()
            else:
                return "Try again"
        elif c == 'from tail' :
            if x == 'en':
                self.enqueue(y)
            elif x == 'de' :
                self.__queue.pop()
            else:
                return "Try again"
        else : return "Try again"
```