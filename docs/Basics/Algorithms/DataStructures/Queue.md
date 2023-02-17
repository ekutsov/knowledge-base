# Queue
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