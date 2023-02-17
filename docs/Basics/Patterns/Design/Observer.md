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


Реальным примером паттерна "Observer" в C# может быть приложение фондового рынка. В этом примере класс Subject представляет акцию и ее состояние, такое как текущая цена и объем торгов. Класс Observer представляет биржевого трейдера, который интересуется состоянием акции, а класс ConcreteObserver представляет конкретного трейдера, который подписался на обновления акции.

Вот пример:

```cs
class Stock : Subject
{
    private string symbol;
    private double price;
    private double volume;

    public Stock(string symbol, double price, double volume)
    {
        this.symbol = symbol;
        this.price = price;
        this.volume = volume;
    }

    public double Price
    {
        get { return price; }
        set
        {
            price = value;
            NotifyAllObservers();
        }
    }

    public double Volume
    {
        get { return volume; }
        set
        {
            volume = value;
            NotifyAllObservers();
        }
    }
}

класс Trader : Observer
{
    private string name;

    public Trader(string name, Stock stock)
    {
        this.name = name;
        this.subject = stock;
        this.subject.Attach(this);
    }

    public override void Update()
    {
        Stock stock = (Stock)subject;
        Console.WriteLine("Трейдер: " + name + ", Stock: " + stock.symbol + ", Price: " + stock.Price + ", Volume: " + stock.Volume);
    }
}

класс Program
{
    static void Main(string[] args)
    {
        Stock stock = new Stock("AAPL", 100.0, 1000.0);
        Trader trader1 = new Trader("John Doe", stock);
        Trader trader2 = new Trader("Jane Smith", stock);

        stock.Price = 110.0;
        stock.Volume = 2000.0;

        Console.Read();
    }
}
```

В этом примере каждый раз, когда цена или объем акции изменяется, будет вызываться метод Update, и трейдеры будут уведомлены об изменении. Трейдеры смогут увидеть символ акции, текущую цену и объем проданных акций.
