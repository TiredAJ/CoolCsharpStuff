---
tags:
  - Tuples
---
Tuples are a quick and lightweight way to make simple data types. One was sneakily implemented in [[Generics & Boxing]]'s CargoContainer class:
```C#
private List<(DateTime TimeStamp, string Action)> Log;
```

The (DateTime TimeStamp, string Action) is the tuple, making *Log* a list of tuples, specially a list of tuples that store *DateTime* and a *string*.
With Tuples like this, you can also define names for the items, so the *DateTime* is named “TimeStamp” and the *string* “Action”.

Assigning data to tuples are quite easy, provided the types match, all you need to do is encase them in (brackets):
```C#
Log.Add((DateTime.Now, "Cargo Encased"));
```

*Log* adds a new tuple that stores the current date and time, as well as the message “Cargo Encased”.

Accessing data from a tuple is quite easy too, to get the timestamp of the first action we can use:
```C#
Console.WriteLine(ChocContainer.GetLog().First().TimeStamp);
```
*(`First()` just returns the first element int the list)*. The above will output
```
14/11/2023 15:32:49
```

We can also throw the log in [[Generics & Boxing]]'s *Print()* function:
```C#
Print<(DateTime, string)>(ChocContainer.GetLog());
```

```
(14/11/2023 15:34:10, Cargo Encased)
(14/11/2023 15:34:12, Cargo Accessed)
```
(a 2 second `Thread.Sleep()` was thrown in between encasing and accessing).

[Return to Home](Home)
