# Observer

Модель **Observer** - это модель проектирования, в которой объект, называемый субъектом, ведет список своих зависимых объектов, называемых наблюдателями, и автоматически уведомляет их о любых изменениях в своем состоянии.

Вот пример паттерна **Observer** на языке C#:

```cs
class Subject
{
    private List<Observer> observers = new List<Observer>();
    private int state;

    public int State
    {
        get { return state; }
        set
        {
            state = value;
            NotifyAllObservers();
        }
    }

    public void Attach(Observer observer)
    {
        observers.Add(observer);
    }

    public void NotifyAllObservers()
    {
        foreach (Observer observer in observers)
        {
            observer.Update();
        }
    }
}

abstract class Observer
{
    protected Subject subject;
    public abstract void Update();
}

class ConcreteObserver : Observer
{
    public ConcreteObserver(Subject subject)
    {
        this.subject = subject;
        this.subject.Attach(this);
    }

    public override void Update()
    {
        Console.WriteLine("Observer: " + this.GetHashCode() + ", State: " + subject.State);
    }
}

class Program
{
    static void Main(string[] args)
    {
        Subject subject = new Subject();
        new ConcreteObserver(subject);
        new ConcreteObserver(subject);
        new ConcreteObserver(subject);

        subject.State = 5;
        subject.State = 10;

        Console.Read();
    }
}
```
