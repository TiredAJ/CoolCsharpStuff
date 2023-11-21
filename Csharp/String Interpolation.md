---
tags:
  - StringInterpolation
---
Very simply, this is a super useful thing in C#, it allows you to easily incorporate variables into strings. You’ve seen examples in previous sections, but say we had the total of the basket from [LINQ](_LINQ): 
```C#
float Total = ShoppingBasket
	.Select(X => X.Price)
	.Sum();
```

... and wanted to display it to the terminal with a message, we could use:
```C#
Console.WriteLine($"The total is {Total:C}");
```

The dollar sign before the string tells the compiler it’s an interpolated string (Obsidian markdown ignores this though :/), meaning we can use {curly braces} to pop in a variable. We also use `:C` to format it as currency. This outputs:
```
The total is £19.14
```

Like _Console.WriteLine()_ (by itself), it secretly calls _.ToString()_ on the object you put in the {curly braces} (that’s why _ToString()_ is overridden in the [Item class](_LINQ)). We’re not restricted to objects with this, we can also call functions in it and it’ll output the result of the function:
```C#
Console.WriteLine($"There are {ShoppingBasket.Count()} items(s) in the basket");
```

```
There are 16 item(s) in the basket
```

[Return to Home](Home)
