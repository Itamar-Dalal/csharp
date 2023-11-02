# asynchronous
C# and .NET Framework (4.5 & Core) support asynchronous programming using some native functions, classes, and reserved keywords.
In asynchronous programming, the code gets executed in a thread without having to wait for an I/O-bound or long-running task to finish.

There are two primary keywords for writing asynchronous code in c#:

<b>Async (Asynchronous):</b>
This keyword is used to declare a method as asynchronous. An asynchronous method is one that can perform tasks without blocking the main program's execution. Instead of waiting for a long-running operation to complete, the program can continue with other tasks and return to the asynchronous operation when it's finished. This is especially useful for I/O-bound operations like file reading or network requests.

<b>Await:</b>
Await is used within an asynchronous method and is followed by an asynchronous operation. It tells the program to pause execution at that point until the operation is completed. While waiting for the operation to finish, the CPU can be utilized for other tasks, making your code more efficient. Await essentially ensures that the result of the asynchronous operation is available before proceeding with the rest of the method.
<u>Example of an Asynchronous Program in C#:</u>
```c#
using System;
using System.Threading.Tasks;

namespace Asynchronous
{
    internal class Program
    {
        static async Task Main(string[] args)
        {
            await LongProcessAsync();
            ShortProcess();
        }

        static async Task LongProcessAsync()
        {
            Console.WriteLine("LongProcess Started");

            await Task.Delay(4000); // hold execution for 4 seconds

            Console.WriteLine("LongProcess Completed");
        }

        static void ShortProcess()
        {
            Console.WriteLine("ShortProcess Started");

            // Do something here

            Console.WriteLine("ShortProcess Completed");
        }
    }
}
```
The output will be:
```
LongProcess Started
ShortProcess Started
ShortProcess Completed
LongProcess Completed
```
Here's a more complex example:
```c#
static async Task Main(string[] args)
{
    Task<int> result1 = LongProcess1();
    Task<int> result2 = LongProcess2();
    
    //do something here
    Console.WriteLine("After two long processes.");

    int val = await result1; // wait untile get the return value
    DisplayResult(val);

    val = await result2; // wait untile get the return value
    DisplayResult(val);

    Console.ReadKey();
}

static async Task<int> LongProcess1()
{
    Console.WriteLine("LongProcess 1 Started");

    await Task.Delay(4000); // hold execution for 4 seconds

    Console.WriteLine("LongProcess 1 Completed");

    return 10;
}

static async Task<int> LongProcess2()
{
    Console.WriteLine("LongProcess 2 Started");

    await Task.Delay(4000); // hold execution for 4 seconds

    Console.WriteLine("LongProcess 2 Completed");

    return 20;
}

static void DisplayResult(int val)
{
    Console.WriteLine(val);
}
```
The output will be: 
```
LongProcess 1 Started
LongProcess 2 Started
After two long processes.
LongProcess 2 Completed
LongProcess 1 Completed
10
20
```
In the above program, we do await result1 and await result2 just before we need to pass the return value to another method.

Thus, you can use async, await, and Task to implement asynchronous programming in .NET Framework or .NET Core using C#.

Source: <a href="https://www.tutorialsteacher.com/articles/asynchronous-programming-with-async-await-task-csharp">https://www.tutorialsteacher.com/articles/asynchronous-programming-with-async-await-task-csharp</a><br/>
You can read more in Microsoft c# guide: <a href="https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming">https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming</a>
