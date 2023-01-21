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
Это структура данных типа "последний в первом" (LIFO), в которой элементы добавляются и удаляются с вершины стека. Это означает, что последний элемент, добавленный в стек, удаляется первым.

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
