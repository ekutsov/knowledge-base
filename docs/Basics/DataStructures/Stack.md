<sub>[Главная](../../index.md) / [Основы программирования](../README.md) / [Структуры данных](./README.md) / **Stack** </sub>

# Stack
Это структура данных типа "last-in-first-out" (LIFO), в которой элементы добавляются и удаляются с вершины стека. Это означает, что последний элемент, добавленный в стек, удаляется первым.

Вот пример базовой реализации стека в C#:

  ```csharp
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

Эта реализация стека позволяет вам вставлять элементы в стек, вытаскивать элементы из стека, заглядывать в верхний элемент стека, проверять, пуст ли стек, и печатать элементы стека.

Стеки часто используются в реальных сценариях, таких как:

- Реализация функции отмены/повтора в текстовых редакторах или редакторах изображений.
- Отслеживание вызовов функций в стеке вызовов в языках программирования.
- Выполнение синтаксического разбора и оценки выражений в языках программирования.
- Сохранение состояния веб-страниц в веб-браузерах.

Важно отметить, что стек имеет временную сложность O(1) для операций push, pop и peek, и он эффективен для этих операций. Однако он имеет временную сложность O(n) для операций поиска и удаления, поэтому это не лучшая структура данных для этих операций.