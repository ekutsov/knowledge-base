# Tree
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
