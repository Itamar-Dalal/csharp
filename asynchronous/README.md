# asynchronous
C# and .NET Framework (4.5 & Core) supports asynchronous programming using some native functions, classes, and reserved keywords.

In asynchronous programming, the code gets executed in a thread without having to wait for an I/O-bound or long-running task to finish.
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

