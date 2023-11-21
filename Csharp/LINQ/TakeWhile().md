---
tags:
  - LINQ
---
_TakeWhile()_ collects elements while a condition is true, for example, if I wanted to collect all the elements before paracetamol, but I didn’t know where it was in the list, I could use:
```C#
List<Item> BeforeParacetamol = ShoppingBasket.TakeWhile(X => !X.Name.Contains("Paracetamol")).ToList();
```

So the condition is, if X.Name doesn’t contain “Paracetamol”. This returns:
```
Dairy Milk - 360g       £3.50
Tesco Finest Sea Salt & Chardonnay Vinegar Crisps 150G  £1.35
2 Custard Slices        £1.65
Stockwell & co Custard 385g     £0.58
Stockwell & co Custard 385g     £0.58
Stockwell & co Rice Pudding 400g        £0.25
Stockwell & co Rice Pudding 400g        £0.25
```

> [!info]
> There’re probably better use cases for this function, but this is something with the demo data.

[Return to LINQ](_LINQ.md)

[Return to Home](Home)
