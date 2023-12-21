---
tags:
  - Threads
  - Atomicity
  - Interlocked
---
## Atomicity
In C#, reading and writing (assignment) any of the following types are guaranteed to be atomic:

|  bool   | char  | byte   | sbyte  | short                  |
|:--------|:------|:-------|:--------|:------------------|
| ushort | uint   | int     | float    | reference types  |

Other operations such as Incrementing aren't atomic and so require specific functions to complete.
## Increment() & Decrement()
With incrementing and decrementing, the [Docs](https://learn.microsoft.com/en-us/dotnet/api/system.threading.interlocked?view=net-8.0#remarks) mention how they aren't atomic operations as it requires multiple instructions on most systems; Load value -> (inc)/(dec)rement the value -> store new value.

The `Increment()` function from `Interlocked` allows for incrementing values across threads. The example below increments an index from one thread, while another prints out the string at the index in `Vals`
```C#
public static int Index = 0;
public static string[] Vals =
{
    "Invidunt", "eos", "diam", "justo", "clita", "nonumy", "magna",
    "gubergren", "amet", "nulla", "et", "nonumy", "feugiat", "clita",
    "augue", "rebum", "vero", "duis", "ipsum", "ut"
};

private static Thread TIncrementer = new Thread(Incrementer);
private static Thread TPrinter = new Thread(Printer);

static void Main(string[] args)
{
    TIncrementer.Start();
    TPrinter.Start();
}

private static void Incrementer()
{
    while (true)
    {
        if (Index < 19)
        { Interlocked.Increment(ref Index); }
        else
        { Index = 0; }

        Thread.Sleep(200);
    }
}

private static void Printer()
{
    while (true)
    {
        Console.WriteLine(Vals[Index]);
        Thread.Sleep(200);
    }
}
```

`Interlocked.Decrement()` does the same, just decrementing.

