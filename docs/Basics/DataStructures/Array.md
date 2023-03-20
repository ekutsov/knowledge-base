<sub>[Главная](../../index.md) / [Основы программирования](../README.md) / [Структуры данных](./README.md) / **Array** </sub>

# Array

Массив - это набор элементов одного типа данных, хранящихся в смежных областях памяти. Они обычно используются для хранения и манипулирования коллекциями данных, такими как списки или таблицы.

Ниже приведен пример базовой реализации массива в C#:

  ```cs
  class ArrayExample {
    private int[] array;

    public ArrayExample(int size) {
        array = new int[size];
    }

    public void Insert(int index, int data) {
        if (index < 0 || index >= array.Length) {
            Console.WriteLine("Invalid index");
            return;
        }

        array[index] = data;
    }

    public int Get(int index) {
        if (index < 0 || index >= array.Length) {
            Console.WriteLine("Invalid index");
            return int.MinValue;
        }

        return array[index];
    }

    public void Delete(int index) {
        if (index < 0 || index >= array.Length) {
            Console.WriteLine("Invalid index");
            return;
        }

        for (int i = index; i < array.Length - 1; i++) {
            array[i] = array[i + 1];
        }
    }

    public void PrintArray() {
        for (int i = 0; i < array.Length; i++) {
            Console.Write(array[i] + " ");
        }
    }
}
  ```
  
Эта реализация массива позволяет вставлять элементы в массив, получать элементы из массива, удалять элементы из массива и выводить элементы массива.

Массивы часто используются в реальных сценариях, таких как:

- Хранение и манипулирование большими объемами данных.
- Реализация структур данных, таких как стеки и очереди.
- Хранение и манипулирование данными в базах данных и других системах управления данными.
- Реализация математических операций, таких как матричные операции.

Важно отметить, что временная сложность операций с массивами, таких как поиск, вставка и удаление, обычно составляет O(n), поскольку в худшем случае необходимо пройти весь массив. Однако для доступа к элементу по его индексу это время равно O(1), что делает массивы хорошими для операций произвольного доступа.