---
tags:
  - Var
  - Generics
---
The var keyword is useful if you’re not sure what type a function is returning or if you just don’t want to specify the type of a variable. I believe at compilation, the compiler works out what type it should be and substitutes it in.
They keyword is used by default in foreach() loops:
```C#
static void Print<T>(List<T> _L)
{
    foreach (var I in _L)
    {Console.WriteLine(I.ToString());}
}
```

(With inline hints enabled, it states what it’s type is. generic T in this case. Find out more here [[Generics & Boxing]]).
 
It’s quite versatile, you can use it like a normal type. For example you can use it to hold the output of a function:
```C#
var Entity = GetObject("23ab23baaa2381");
```


[Check out *Generics*](Generics%20&%20Boxing.md)

[Return to Home](Home)
