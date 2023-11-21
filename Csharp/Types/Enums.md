---
tags:
  - Enums
  - Dictionaries
---
Enums are quite a nice way of defining a small set of interchangeable things, for example, you could store the days of the week like:
```C#
public enum Weekdays
{
	Monday,
	Tuesday,
	Wednesday,
	Thursday,
	Friday,
	Saturday,
	Sunday
}
```

With them defined like this, you have a tight control on what any _Weekdays_ variable can be. For example:
```C#
private static Weekdays DayOff;
```

The variable *DayOff* can only be one of the options we’ve defined above, like Saturday:
```C#
private static Weekdays DayOff = Weekdays.Saturday;
```

At it’s base, enums are some kinda of “[integral numeric](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) type”, but you can define what type that is:
```C#
public enum Weekdays : int
{
	Monday = 1,
	Tuesday = 2,
	Wednesday = 3,
	Thursday = 4,
	Friday = 5,
	Saturday = 6,
	Sunday = 7
}
```

This makes enums very useful for collections. You could use _WeekDays_ to access indexes of an array, or use them as keys for a dictionary:
```C#
private static string[] Tasks = new string[7];
private static Dictionary<Weekdays, string> OtherTasks = new Dictionary<Weekdays, string>()
{
	{Weekdays.Monday, "Bins"},
	{Weekdays.Tuesday, "Gaming"},
};

static void Main(string[] args)
{
	Tasks[(int)Weekdays.Monday] = "Classes";
	string TodaysTask = OtherTasks[Weekdays.Tuesday]
}
```

[Return to Home](Home.md)
