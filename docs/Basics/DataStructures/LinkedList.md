<sub>[Главная](../../index.md) / [Основы программирования](../README.md) / [Структуры данных](./README.md) / **Linked List** </sub>

# Linked list
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