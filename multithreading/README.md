# Multi-Threading in C#

C# is a multi-paradigm programming language that supports several programming styles, including procedural, object-oriented, and functional programming.
One of the essential features of C# is its support for multithreading, which enables developers to write applications that can perform multiple tasks concurrently.

Here are some common C# threading commands and their explanations:

- **Thread class**:
    - The `Thread` class is the foundation for working with threads in C#. You can create and manage threads using this class.

- **Thread.Start()**:
    - Use `Thread.Start()` to begin the execution of a thread. It starts running the code provided in the thread's delegate or method.

- **Thread.Join()**:
    - `Thread.Join()` is used to wait for a thread to complete its execution. It's helpful when you need to ensure that a thread finishes before continuing with the main thread.

- **Thread.Sleep()**:
    - `Thread.Sleep()` suspends the execution of the current thread for a specified amount of time. It's useful for introducing delays or pausing threads.

- **Thread.Abort()**:
    - `Thread.Abort()` is used to forcibly terminate a thread. However, it's not recommended because it can lead to unpredictable behavior.

- **Thread.IsAlive**:
    - `Thread.IsAlive` is a property that indicates whether a thread is still running.

- **Thread.Priority**:
    - `Thread.Priority` allows you to set the priority of a thread, affecting its scheduling in the operating system. Common values include `ThreadPriority.Lowest`, `ThreadPriority.Normal`, and `ThreadPriority.Highest`.

- **ThreadPool**:
    - C# provides a built-in thread pool, which you can use to efficiently manage a pool of worker threads for executing tasks.

- **Task and async/await**:
    - In modern C# programming, you often use the `Task` class and the `async/await` keywords for asynchronous programming. These are higher-level abstractions that simplify working with asynchronous operations.
      You can read more in the asynchronous repo.

- **Parallel class**:
    - The `Parallel` class offers methods for parallelizing operations, such as `Parallel.ForEach` and `Parallel.For`, making it easier to work with multi-threading in certain scenarios.
    - 
- **Locking with `lock`**:
    - You can use the `lock` statement to protect shared resources and prevent race conditions in multi-threaded programs. It ensures that only one thread can execute a critical section of code at a time.

Here’s an example that demonstrates a multi-threaded program where each thread performs a specific task:
using System;
using System.Threading;
using System.Collections.Generic;


class Program
{
    private static object lockObject = new object();
    private static int counter = 0;

    static void Main()
    {
        Thread[] threads = new Thread[5];

        for (int i = 0; i < 5; i++)
        {
            var thread = new Thread(() => PerformTask(i));
            threads[i] = thread;
            thread.Start();
        }

        foreach (var thread in threads)
        {
            thread.Join();
        }

        Console.WriteLine("Main Thread Finished");
    }

    static void PerformTask(int threadId)
    {
        for (int i = 0; i < 5; i++)
        {
            // Simulate some work
            Thread.Sleep(100);

            // Increment and print the counter using a lock
            lock (lockObject)
            {
                counter++;
                Console.WriteLine($"Thread {threadId}: Counter = {counter}");
            }
        }
    }
}
```
In this example:

Multiple threads are created and started to perform the PerformTask method.
Thread.Sleep(100) is used to simulate work or delay in each thread.
lock is employed to ensure that only one thread can increment and print the counter variable at a time.
Thread.Join() is used to wait for all threads to finish before the main thread continues.
The counter variable is safely incremented and displayed by the threads.
