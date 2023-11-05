# Language Integrated Query (LINQ)
Language-integrated query (LINQ) is a powerful set of technologies based on the integration of query capabilities directly into the C# language.
LINQ is a uniform query syntax in C# to retrieve data from different sources and formats.

LINQ has many uses:

<img src="https://www.tutorialsteacher.com/Content/images/linq/linq-usage.PNG"/>

LINQ queries return the results as objects. <br/>
<img src="https://www.tutorialsteacher.com/Content/images/linq/linq-execution.PNG"/>
<br/>

The following example demonstrates a simple LINQ query that gets all strings from an array that contains 'a'.
```c#
// Data source
string[] names = {"Bill", "Steve", "James", "Mohan" };

// LINQ Query 
var myLinqQuery = from name in names
                where name.Contains('a')
                select name;
    
// Query execution
foreach(var name in myLinqQuery)
    Console.Write(name + " ");
```
You will not get the result of a LINQ query until you execute it.
LINQ query can be executed in multiple ways, here we used foreach loop to execute our query stored in myLinqQuery.
The foreach loop executes the query on the data source, gets the result, and then iterates over the result set.

For more information about the syntax of LINQ, visit this website: https://www.tutorialsteacher.com/linq

