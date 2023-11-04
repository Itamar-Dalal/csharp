# Dependency Injection in C#
## Introduction
<b>Dependencies</b> - external libraries, modules, or components (class, function, interface...) that your project relies on to function correctly.

Dependency Injection (DI) involves injecting a dependency's code into a component rather than calling it directly.
This helps decouple components and allows for easier testing and maintenance.

## The Benefits of Dependency Injection
### Loose Coupling:
<b>Coupling</b> - describes the relationship between modules in C#, how the classes and objects are connected, and also how dependent they are on each other.
Dependency injection promotes loose coupling by removing the direct dependencies between classes.

### Testability:
With dependency injection, it becomes simpler to write unit tests for individual components.
By injecting mock or test implementations of dependencies, developers can isolate the component under test, making it easier to verify its behavior.

### Reusability:
Dependency injection promotes code reuse. components can be reused in different contexts, increasing the overall modularity and maintainability of the codebase.

## Implementation of dependency injection in C#
### Constructor Injection
One of the most common approaches to dependency injection in C# is constructor injection. In this approach, dependencies are provided through a class's constructor. Let's consider a simple example:
```c#
public class CustomerService
{
    private readonly ICustomerRepository _customerRepository;
    public CustomerService(ICustomerRepository customerRepository)
    {
        _customerRepository = customerRepository;
    }
    // ...
}
```
Here, the CustomerService class depends on an interface ICustomerRepository. The dependency is injected through the constructor, allowing different implementations of ICustomerRepository to be supplied.

### Property Injection
Another approach is property injection, where dependencies are exposed as public properties and are set externally. While this approach offers flexibility, it may make it less clear what dependencies a class requires. Here's an example:
```c#
public class CustomerService
{
    public ICustomerRepository CustomerRepository { get; set; }
    // ...
}
```
### Method Injection
Method injection involves passing dependencies through methods instead of constructors or properties. This approach is useful when a dependency is required for a specific method but not for the entire lifetime of the object. Here's an example:
```c#
public class CustomerService
{
    // ...
    public void SetCustomerRepository(ICustomerRepository customerRepository)
    {
        _customerRepository = customerRepository;
    }
    // ...
}
```
For more information, check out these sources:
<ul>
https://youtu.be/J1f5b4vcxCQ?si=PIdiymCJxBKq9l4U
  <br/>
https://medium.com/@avinash.dhumal/understanding-dependency-injection-a-practical-guide-with-c-examples-aee44eacee32
</ul>
