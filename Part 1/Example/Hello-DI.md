 # Basic Hello - DI example
 ```
 internal interface IMessageWriter
    {
        void Write(string message);
    }

    internal class ConsoleMessageWritter : IMessageWriter
    {
        public void Write(string message)
        {
            {
                Console.WriteLine(message);
            }
        }
    }

    internal class Salutation
    {
        private readonly IMessageWriter _writer;

        public Salutation(IMessageWriter writer)
        {
            if (writer == null)
            {
                throw new ArgumentNullException(nameof(writer));
            }
            this._writer = writer;
        }

        public void Exclaim()
        {
            this._writer.Write("Hello DI!");
        }
    }

    internal class Program
    {
        private static void Main(string[] args)
        {
            IMessageWriter writer = new ConsoleMessageWritter();
            var salutation = new Salutation(writer);
            salutation.Exclaim();

            Console.ReadKey();
        }
    }
``` 
# Hello DI with secure message writer example
```
using System;
using System.Security.Principal;

namespace HelloDI
{
    internal interface IMessageWriter
    {
        void Write(string message);
    }

    internal class ConsoleMessageWritter : IMessageWriter
    {
        public void Write(string message)
        {
            {
                Console.WriteLine(message);
            }
        }
    }

    internal class SecureMessageWritter : IMessageWriter
    {
        private readonly IMessageWriter _writer;
        private readonly IIdentity _identity;

        public SecureMessageWritter(IMessageWriter writer, IIdentity identity)
        {
            if (writer == null)
                throw new ArgumentNullException();
            if (identity == null)
                throw new ArgumentNullException();

            _writer = writer;
            _identity = identity;
        }

        public void Write(string message)
        {
            if (_identity.IsAuthenticated)
            {
                _writer.Write(message);
            }
        }
    }

    internal class Salutation
    {
        private readonly IMessageWriter _writer;

        public Salutation(IMessageWriter writer)
        {
            if (writer == null)
            {
                throw new ArgumentNullException(nameof(writer));
            }
            this._writer = writer;
        }

        public void Exclaim()
        {
            this._writer.Write("Hello DI!");
        }
    }

    internal class Program
    {
        private static void Main(string[] args)
        {
            IMessageWriter writer = new SecureMessageWritter(new ConsoleMessageWritter(), WindowsIdentity.GetCurrent());
            var salutation = new Salutation(writer);
            salutation.Exclaim();

            Console.ReadKey();
        }
    }
}
```
