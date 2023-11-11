# C# Design Patterns
Design pattern in software engineering is a general, reusable solution to a commonly occurring problem in software design.
A design pattern suggests a specific implementation for the specific object-oriented programming problem.

## Design Patterns Overview

Design patterns provide solutions to common software design problems. They are categorized into three groups: Creational, Structural, and Behavioral.

### Creational Design Patterns

- **Singleton**: Singleton is a technique that's used in OOP programming in order to create a class that has only one instance.
  For example:
```csharp
using System;
namespace ConsoleApp76
{
    sealed class example // Sealed – meaning that no class can inherit from this class (not related to Singleton)
    {
        private static example ob = null;
        private int value;
        private example(int value)
        {
            this.value = value;
        }
        public static example CreateExample(int value)
        {
            if(ob == null)
        {
                ob = new example(value);
            }
            return ob;
        }
        public int getvalue()
        {
            return this.value;
        }
    }

class Program
    {
        static void Main(string[] args)
        {
            example ob1 = example.CreateExample(10);
            example ob2 = example.CreateExample(15);
            Console.WriteLine(ob2.getvalue()); // same instance -> printing 10
        }
    }
}
```

- **Abstract Factory (Interface)**: Interface in C# is a blueprint of a class. It's like an abstract class because all the methods that are declared inside the interface are abstract methods. It cannot have a method body and cannot be instantiated.
It's used to achieve multiple inheritance which can't be achieved by class. It is used to achieve full abstraction because it cannot have a method body.
The class or struct that implements the interface must provide the implementation of all the methods declared inside the interface.
For example:
```csharp
// declaring an interface
public interface A {
     
    // method of interface
    void mymethod1();
    void mymethod2();
}
 
// The methods of interface A
// is inherited into interface B
public interface B : A {
     
    // method of interface B
    void mymethod3();
}
 
 
// Below class is inheriting
// only interface B
// This class must
// implement both interfaces
class Geeks : B
{
     
    // implementing the method
    // of interface A
    public void mymethod1()
    {
        Console.WriteLine("Implement method 1");
    }
     
    // Implement the method
    // of interface A
    public void mymethod2()
    {
        Console.WriteLine("Implement method 2");
    }
     
    // Implement the method
    // of interface B
    public void mymethod3()
    {
        Console.WriteLine("Implement method 3");
    }
}
```
- **Builder**: Separates the construction of a complex object from its representation.
  For example:
```csharp
public class Computer
{
    public string CPU { get; set; }
    public int RAM { get; set; }
    public string Storage { get; set; }
}

public class ComputerBuilder
{
    private Computer computer;

    public ComputerBuilder()
    {
        computer = new Computer();
    }

    public ComputerBuilder SetCPU(string cpu)
    {
        computer.CPU = cpu;
        return this;
    }

    public ComputerBuilder SetRAM(int ram)
    {
        computer.RAM = ram;
        return this;
    }

    public ComputerBuilder SetStorage(string storage)
    {
        computer.Storage = storage;
        return this;
    }

    public Computer Build()
    {
        return computer;
    }
}
```
Usage:
```csharp
var builder = new ComputerBuilder();
// method chaining (it works because the functions return "this")
var customComputer = builder
    .SetCPU("Intel i7")
    .SetRAM(16)
    .SetStorage("512GB SSD")
    .Build();
```
- **Factory Method**: Defines an interface for creating an object, but leaves the choice of its type to the subclasses.
  For example:
```csharp
public abstract class Document
{
    public abstract void Open();
    public abstract void Close();
}

public class PDFDocument : Document
{
    public override void Open()
    {
        Console.WriteLine("Opening PDF document");
    }

    public override void Close()
    {
        Console.WriteLine("Closing PDF document");
    }
}

public class TextDocument : Document
{
    public override void Open()
    {
        Console.WriteLine("Opening Text document");
    }

    public override void Close()
    {
        Console.WriteLine("Closing Text document");
    }
}

public interface DocumentFactory
{
    Document CreateDocument();
}

public class PDFDocumentFactory : DocumentFactory
{
    public Document CreateDocument()
    {
        return new PDFDocument();
    }
}

public class TextDocumentFactory : DocumentFactory
{
    public Document CreateDocument()
    {
        return new TextDocument();
    }
}
```
Usage:
```csharp
DocumentFactory pdfFactory = new PDFDocumentFactory();
Document pdfDoc = pdfFactory.CreateDocument();
pdfDoc.Open();
pdfDoc.Close();
```
- **Prototype**: Creates new objects by copying an existing object, known as a prototype.
  For example:
```csharp
public interface IShape
{
    IShape Clone();
    void Draw();
}

public class Circle : IShape
{
    public int Radius { get; set; }

    public IShape Clone()
    {
        return new Circle { Radius = this.Radius };
    }

    public void Draw()
    {
        Console.WriteLine("Drawing a circle with radius " + Radius);
    }
}
```
Usage:
```csharp
IShape originalCircle = new Circle { Radius = 5 };
IShape clonedCircle = originalCircle.Clone();
originalCircle.Draw();
clonedCircle.Draw();
```
Note: I won't give any more code examples, those interested in seeing how this is implemented can search on the internet.
### Structural Design Patterns

- **Adapter**: Allows the interface of an existing class to be used as another interface.
- **Bridge**: Separates an object's abstraction from its implementation, so they can vary independently.
- **Composite**: Composes objects into tree structures to represent part-whole hierarchies.
- **Decorator**: Adds responsibilities to objects dynamically without altering their code.
- **Facade**: Provides a simplified interface to a set of interfaces in a subsystem.
- **Flyweight**: Minimizes memory usage or computational expenses by sharing as much as possible with related objects.
- **Proxy**: Provides a surrogate or placeholder for another object to control access to it.

### Behavioral Design Patterns

- **Chain of Responsibility**: Passes a request along a chain of handlers, each handling it or passing it to the next handler.
- **Command**: Encapsulates a request as an object, thereby allowing for parameterization of clients with queues, requests, and operations.
- **Interpreter**: Provides a way to evaluate language grammar or expressions.
- **Iterator**: Provides a way to access elements of an aggregate object sequentially without exposing its underlying representation.
- **Mediator**: Defines an object that encapsulates how objects interact and communicate with each other.
- **Memento**: Captures an object's internal state to be able to restore it later.
- **Observer**: Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
- **State**: Allows an object to alter its behavior when its internal state changes.
- **Strategy**: Defines a family of algorithms, encapsulates each one, and makes them interchangeable.
- **Template Method**: Defines the skeleton of an algorithm in the base class and lets subclasses override specific steps of the algorithm without changing its structure.
- **Visitor**: Represents an operation to be performed on the elements of an object structure, lets you define a new operation without changing the classes of the elements.
