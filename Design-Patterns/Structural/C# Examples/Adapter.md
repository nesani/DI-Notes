```
    public interface ITarget
    {
        // The Target defines the domain-specific interface used by the client code.
        string GetRequest();
    }
    class Adaptee
    {
        public string GetSpecificRequest()
        {
            return "Specific Request.";
        }
    }

    class Adapter : ITarget
    {
        private readonly Adaptee _adaptee;

        public Adapter(Adaptee adaptee)
        {
            _adaptee = adaptee;
        }

        public string GetRequest() 
        {
            return $"This is '{_adaptee.GetSpecificRequest()}'";
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            var adaptee = new Adaptee();
            var target = new Adapter(adaptee);

            Console.WriteLine("Adaptee interface is incompatible with the client.");
            Console.WriteLine("But with adapter client can call it's method.");

            Console.WriteLine(target.GetRequest());

            Console.ReadKey();
        }
    }
```