---
tags:
  - Dictionaries
---
Dictionaries are one of my favourite C# collections. At their base they’re a hash table, but it’s use of generics makes it so much more useful. It allows you to assign a _key_ to an object, and access it by that key very quickly:

> “_Retrieving a value by using its key is very fast, close to O(1), because the Dictionary<TKey,TValue> class is implemented as a hash table._”[^1]
	-- C# [Docs](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=net-7.0)

[^1]: “The speed of retrieval depends on the quality of the hashing algorithm of the type specified for TKey.”

To use a dictionary, you need to decide what it’s storing (it’s value) and what you want to use to access what it’s storing (the key). It could store a custom “Employee” class as the value and an integer key representing the employee’s ID.

```C#
private static Dictionary<int, Employee> Employees = new Dicitonary<int, Employee>();
//                              ^ type of the value
//                         ^ type of the key
private static int ID = 0;

static void Main(string[] args)
{Employees.Add(ID, new Employee("John Smith", ID++));} 

public class Employee
{
	public string Name {get; set;}
	public int ID {get; private set;}

	public Employee(string _Name, int _ID)
	{
		Name = _Name
		ID = _ID
	}
}
```

The code above defines an Employee class and a dictionary made up of an int key and Employee value. We’re also adding an element to the dictionary, one “John Smith”. The variable _ID_ is used as the key and the employee’s internal ID and auto increments when the Employee object is created. We can access John from the dictionary like this:
```C# 
Employee John = Employees[0];
```

We know John has the key 0, so we can access them from the dictionary like an array.

> [!info]
> With how dictionaries work, **Keys must be unique**, you cannot have two keys the same, else the compiler will tell you off or your program'll crash. This is because of the dictionary’s internal hash table hashing keys when they’re added.

[Return to Home](Home.md)
