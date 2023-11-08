# C# Design Patterns
Design pattern in software engineering is a general, reusable solution to a commonly occurring problem in software design.
A design pattern suggests a specific implementation for the specific object-oriented programming problem.

## Design Patterns Overview

Design patterns provide solutions to common software design problems. They are categorized into three groups: Creational, Structural, and Behavioral.

### Creational Design Patterns

- **Singleton**: Singleton is a technique that's used in OOP programming in order to create a class that has only one instance.
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

- **Abstract Factory**: Provides an interface for creating families of related or dependent objects.
- **Builder**: Separates the construction of a complex object from its representation.
- **Factory Method**: Defines an interface for creating an object, but leaves the choice of its type to the subclasses.
- **Prototype**: Creates new objects by copying an existing object, known as a prototype.

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
