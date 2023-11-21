---
tags:
  - Properties
---
Properties are useful class members in C#. They allow for auto-implemented getters and setters which can be customised if you need:
## Different Access Modifiers
You can have a property that can be publicly read from, but privately set:
```C#
public class Employee
{
	public string Name { get; private set; }
	public Employee(string _Name)
	{Name = _Name}
}
```

With the above, the property “Name” can be read from outside the class, but can only be altered from inside, unless it’s set through the constructor.

Demonstrating this:
![[Pasted image 20231121195415.png | 600]]

Hovering over the red squiggly shows the error CS0272 because the setter is private.
![[Pasted image 20231121195458.png | 600]]

Properties don’t just work with public and private, you can choose other [_Access Modifiers_](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers#summary-table) like _internal_, _protected_ etc. You can also leave them blank and they’ll both use whatever access modifier the member is set to.


## Hidden Fields
Using properties with hidden fields can give you extra control with the assignment/reading of a value.
```C#
public class Archive
{
	private string _SecretData = "The cake is a lie";
	private int ReadCounter = 0, WriteCounter = 0;

	public string Secret Data
	{
		get
		{
			ReadCounter++;
			return _SecretData;
		}
		set
		{
			WriteCounter++;
			_SecretData = value;
		}
	}

	public void Report()
	{
		Console.WriteLine($"Secret was read from {ReadCounter} times, ") +
		$"and written to {WriteCounter} times")
	}
}
```

The above keeps a counter of how often the secret has been accessed. With the code below...
```C#
private static Archive Arc = new Archive();

static void Main(string[] args)
{
	var Temp = Arc.SecretData;
	Temp = Arc.SecretData;
	Temp = Arc.SecretData;

	Arc.SecretData = "The Birds Work for the Bourgeoisie";

	Arc.Report();
}
```
... *Report()* will print 3 and 1:
```txt
Secret was read from 3 times, and written to 1 times
```

You can also use it to control the format of data:
```C#
public class DataReport
{
	private double _Temperature = 26.2d;

	public string Temperature
	{
		get => $"{_Temperature}°C";

		set 
		{
			if (!double.TryParse(value, out _Temperature))
			{Console.WriteLine("Value is not a vlaid double!");}
		}
	}
}
```

The use of the *[[out]]* keyword and *[[String Interpolation]]* will both be discussed later.

[Return to Home](Home)
