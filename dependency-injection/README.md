# Dependency Injection in C#
## Introduction
<b>Dependencies</b> - external libraries, modules, or components that your project relies on to function correctly.

Dependency Injection (DI) involves injecting a dependency's code into a component rather than calling it directly.
This helps decouple components and allows for easier testing and maintenance.

## The Benefits of Dependency Injection
### Loose Coupling:
<b>Coupling</b> - describes the relationship between modules in C#, how the classes and objects are connected, and also how dependent they are on each other.
Dependency injection promotes loose coupling by removing the direct dependencies between classes.
Components only depend on abstractions (interfaces or abstract classes), allowing more flexibility when writing the code.

(stopped here)
### Testability:
With dependency injection, it becomes simpler to write unit tests for individual components.
By injecting mock or test implementations of dependencies, developers can isolate the component under test,
making it easier to verify its behavior without external dependencies.

### Reusability:
Dependency injection promotes code reuse. By depending on abstractions rather than concrete implementations,
components can be reused in different contexts, increasing the overall modularity and maintainability of the codebase.

https://youtu.be/J1f5b4vcxCQ?si=PIdiymCJxBKq9l4U
https://medium.com/@avinash.dhumal/understanding-dependency-injection-a-practical-guide-with-c-examples-aee44eacee32
