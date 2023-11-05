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
