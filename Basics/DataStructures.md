# Data structures

## **Linked list**
Это структура данных, состоящая из последовательности элементов, каждый из которых содержит ссылку на следующий элемент списка. Это динамическая структура данных, что означает, что количество элементов в списке может увеличиваться или уменьшаться по мере необходимости.

Ниже приведен пример базовой реализации односвязного списка на языке C#:
<details>
  <summary>Linked list example</summary>
  
  ```cs
class Node {
    public int Data { get; set; }
    public Node Next { get; set; }

    public Node(int data) {
        Data = data;
        Next = null;
    }
}

class LinkedList {
    private Node head;

    public LinkedList() {
        head = null;
    }

    public void InsertFirst(int data) {
        Node newNode = new Node(data);
        newNode.Next = head;
        head = newNode;
    }

    public void InsertLast(int data) {
        if (head == null) {
            head = new Node(data);
            return;
        }

        Node current = head;
        while (current.Next != null) {
            current = current.Next;
        }

        current.Next = new Node(data);
    }

    public void DeleteFirst() {
        if (head == null) {
            return;
        }

        head = head.Next;
    }

    public void DeleteLast() {
        if (head == null) {
            return;
        }

        if (head.Next == null) {
            head = null;
            return;
        }

        Node current = head;
        while (current.Next.Next != null) {
            current = current.Next;
        }

        current.Next = null;
    }

    public void PrintList() {
        Node current = head;
        while (current != null) {
            Console.Write(current.Data + " ");
            current = current.Next;
        }
    }
}
```
</details>

Эта реализация односвязного списка позволяет вставлять элементы в начало или конец списка, удалять элементы из начала или конца списка и обходить список, распечатывая его элементы.

Связные списки широко используются в реальных сценариях, например, в эффективной реализации кэша LRU, отслеживании свободных блоков в управлении памятью и т.д.

Важно отметить, что связанные списки имеют временную сложность O(n) для операций поиска, вставки и удаления, и они не так эффективны, как массивы, когда дело доходит до этих операций. Однако связанные списки более эффективны, когда речь идет о вставке и удалении элементов в начале списка, что является операцией O(1).

## **Stack**
Это структура данных типа "last-in-first-out" (LIFO), в которой элементы добавляются и удаляются с вершины стека. Это означает, что последний элемент, добавленный в стек, удаляется первым.

Вот пример базовой реализации стека в C#:
<details>
  <summary>Stack example</summary>
  
  ```cs
  class Stack {
    private int[] stackArray;
    private int top;

    public Stack(int size) {
        stackArray = new int[size];
        top = -1;
    }

    public void Push(int data) {
        if (top == stackArray.Length - 1) {
            Console.WriteLine("Stack overflow");
            return;
        }

        top++;
        stackArray[top] = data;
    }

    public int Pop() {
        if (top == -1) {
            Console.WriteLine("Stack underflow");
            return int.MinValue;
        }

        int value = stackArray[top];
        top--;
        return value;
    }

    public int Peek() {
        if (top == -1) {
            Console.WriteLine("Stack is empty");
            return int.MinValue;
        }

        return stackArray[top];
    }

    public bool IsEmpty() {
        return top == -1;
    }

    public void PrintStack() {
        if (top == -1) {
            Console.WriteLine("Stack is empty");
            return;
        }

        for (int i = top; i >= 0; i--) {
            Console.Write(stackArray[i] + " ");
        }
    }
  }
  ```
</details>

Эта реализация стека позволяет вам вставлять элементы в стек, вытаскивать элементы из стека, заглядывать в верхний элемент стека, проверять, пуст ли стек, и печатать элементы стека.

Стеки часто используются в реальных сценариях, таких как:

- Реализация функции отмены/повтора в текстовых редакторах или редакторах изображений.
- Отслеживание вызовов функций в стеке вызовов в языках программирования.
- Выполнение синтаксического разбора и оценки выражений в языках программирования.
- Сохранение состояния веб-страниц в веб-браузерах.

Важно отметить, что стек имеет временную сложность O(1) для операций push, pop и peek, и он эффективен для этих операций. Однако он имеет временную сложность O(n) для операций поиска и удаления, поэтому это не лучшая структура данных для этих операций.

## Queue
Это структура данных типа "first-in-first-out" (FIFO), в которой элементы добавляются в конец очереди и удаляются из передней части. Это означает, что первый элемент, добавленный в очередь, первым и удаляется.

Вот пример базовой реализации очереди в C#:

<details>
  <summary>Queue example</summary>
  
  ```cs
  class Queue {
    private int[] queueArray;
    private int front;
    private int rear;
    private int count;

    public Queue(int size) {
        queueArray = new int[size];
        front = 0;
        rear = -1;
        count = 0;
    }

    public void Enqueue(int data) {
        if (count == queueArray.Length) {
            Console.WriteLine("Queue overflow");
            return;
        }

        rear = (rear + 1) % queueArray.Length;
        queueArray[rear] = data;
        count++;
    }

    public int Dequeue() {
        if (count == 0) {
            Console.WriteLine("Queue underflow");
            return int.MinValue;
        }

        int value = queueArray[front];
        front = (front + 1) % queueArray.Length;
        count--;
        return value;
    }

    public int Peek() {
        if (count == 0) {
            Console.WriteLine("Queue is empty");
            return int.MinValue;
        }

        return queueArray[front];
    }

    public bool IsEmpty() {
        return count == 0;
    }

    public void PrintQueue() {
        if (count == 0) {
            Console.WriteLine("Queue is empty");
            return;
        }

        int index = front;
        for (int i = 0; i < count; i++) {
            Console.Write(queueArray[index] + " ");
            index = (index + 1) % queueArray.Length;
        }
    }
  }
  ```
</details>
Эта реализация очереди позволяет записывать элементы в очередь, выписывать элементы из очереди, просматривать первый элемент очереди, проверять, пуста ли очередь, и выводить элементы очереди.

Очереди широко используются в реальных сценариях, таких как:

- Реализация очереди или буфера.
- Планирование задач и заданий в операционных системах.
- Поддержание нескольких соединений в сетевых протоколах.
- Алгоритм первичного поиска в теории графов.
  
Важно отметить, что очередь имеет временную сложность O(1) для операций enqueue, dequeue и peek, и она эффективна для этих операций. Однако она имеет временную сложность O(n) для операций поиска и удаления, поэтому это не лучшая структура данных для этих операций.
  
## Tree
Это иерархическая структура данных, в которой каждый элемент (узел) может иметь один или несколько дочерних элементов. Самый верхний элемент дерева называется корнем, а элементы, не имеющие детей, называются листьями.

Ниже приведен пример базовой реализации бинарного дерева на языке C#:
<details>
  <summary>Tree example</summary>
  
  ```cs
  class Node {
    public int Data { get; set; }
    public Node Left { get; set; }
    public Node Right { get; set; }

    public Node(int data) {
        Data = data;
        Left = null;
        Right = null;
    }
}

class BinaryTree {
    private Node root;

    public BinaryTree() {
        root = null;
    }

    public void Insert(int data) {
        root = InsertHelper(root, data);
    }

    private Node InsertHelper(Node current, int data) {
        if (current == null) {
            current = new Node(data);
            return current;
        }

        if (data < current.Data) {
            current.Left = InsertHelper(current.Left, data);
        } else if (data > current.Data) {
            current.Right = InsertHelper(current.Right, data);
        }

        return current;
    }

    public bool Search(int data) {
        return SearchHelper(root, data);
    }

    private bool SearchHelper(Node current, int data) {
        if (current == null) {
            return false;
        }

        if (current.Data == data) {
            return true;
        }

        if (data < current.Data) {
            return SearchHelper(current.Left, data);
        } else {
            return SearchHelper(current.Right, data);
        }
    }

    public void PreOrderTraversal() {
        PreOrderHelper(root);
    }

    private void PreOrderHelper(Node current) {
        if (current == null) {
            return;
        }

        Console.Write(current.Data + " ");
        PreOrderHelper(current.Left);
        PreOrderHelper(current.Right);
    }
}
  ```
</details>
  
Эта реализация двоичного дерева позволяет вставлять элементы в дерево, искать элементы в дереве и выполнять обход дерева в предварительном порядке.

Деревья широко используются в реальных сценариях, таких как:

- Реализация иерархических структур данных, таких как файловые системы.
- Выполнение таких алгоритмов, как поиск, сортировка и обход в теории графов.
- Реализация деревьев решений в машинном обучении.
- Хранение данных в базах данных и других системах управления данными.
Важно отметить, что временная сложность операций с деревьями, таких как поиск, вставка и удаление, может варьироваться в зависимости от типа дерева и его структуры. Например, временная сложность поиска, вставки и удаления в двоичном дереве поиска в среднем составляет O(log n), но в худшем случае она может быть O(n), если дерево не сбалансировано.
