---
tags:
  - LINQ
---
As sneaked in earlier, we can chain LINQ functions. Say you wanted to have a list of prices in order of least to most expensive, you could use:
```C#
List<float> OnlyPrices = ShoppingBasket    
    .DistinctBy(X => X.Price)
    .Select(X => X.Price)
    .Order()
    .ToList();
```

You don’t have to format it like that ^, but that’s generally how it’s done. Anyway, that’ll result in:
```
0.25
0.35
0.39
0.58
0.89
0.95
1.35
1.65
2
2.5
3.5
```

[Return to LINQ](_LINQ)

[Return to Home](Home)
