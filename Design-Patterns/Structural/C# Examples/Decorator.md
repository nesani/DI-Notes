```
using System;

namespace Decorator_Pattern
{
    // The base Component interface defines operations that can be altered by
    // decorators.
    public abstract class Component
    {
        public abstract string Operation();
    }

    // Concrete Components provide default implementations of the operations.
    // There might be several variations of these classes.
    internal class ConcreteComponent : Component
    {
        public override string Operation()
        {
            return "Component";
        }
    }

    // The base Decorator class follows the same interface as the other
    // components. The primary purpose of this class is to define the wrapping
    // interface for all concrete decorators. The default implementation of the
    // wrapping code might include a field for storing a wrapped component and
    // the means to initialize it.
    internal abstract class BaseDecorator : Component
    {
        protected Component _component;

        public BaseDecorator(Component component)
        {
            _component = component;
        }

        public void SetComponent(Component component)
        {
            _component = component;
        }

        // The Decorator delegates all work to the wrapped component.
        public override string Operation()
        {
            if (_component != null)
            {
                return _component.Operation();
            }
            else
            {
                return string.Empty;
            }
        }
    }

    // Concrete Decorators call the wrapped object and alter its result in some
    // way.
    internal class ConcreteDecoratorA : BaseDecorator
    {
        public ConcreteDecoratorA(Component component) : base(component)
        {
        }

        // Decorators may call parent implementation of the operation, instead
        // of calling the wrapped object directly. This approach simplifies
        // extension of decorator classes.
        public override string Operation()
        {
            return $"ConcreteDecoratorA({base.Operation()})";
        }
    }

    // Decorators can execute their behavior either before or after the call to
    // a wrapped object.
    internal class ConcreteDecoratorB : BaseDecorator
    {
        public ConcreteDecoratorB(Component component) : base(component)
        {
        }

        public override string Operation()
        {
            return $"ConcreteDecoratorB({base.Operation()})";
        }
    }

    public class Client
    {
        public void ClientCode(Component component)
        {
            System.Console.WriteLine("Result: " + component.Operation());
        }
    }

    internal class Program
    {
        private static void Main(string[] args)
        {
            var client = new Client();
            var simple = new ConcreteComponent();

            client.ClientCode(simple);

            // ...as well as decorated ones.
            //
            // Note how decorators can wrap not only simple components but the
            // other decorators as well.

            var decoratorA = new ConcreteDecoratorA(simple);
            var decoratorB = new ConcreteDecoratorB(decoratorA);

            System.Console.WriteLine("Now i got Decorated component");

            client.ClientCode(decoratorB);

            Console.ReadKey();
        }
    }
}
```
