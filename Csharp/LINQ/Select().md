---
tags:
  - LINQ
---
Select is good if you want to “project each element of a sequence into a new form” ([Docs](https://learn.microsoft.com/en-us/dotnet/api/system.linq.enumerable.select?view=net-7.0&redirectedfrom=MSDN#System_Linq_Enumerable_Select__2_System_Collections_Generic_IEnumerable___0__System_Func___0___1__)). For example, if I wanted to get a list of just the names of the items in _ShoppingBasket_, I can use:
```C#
List<string> Names = ShoppingBasket.Select(X => X.Name).ToList();
```
Printed, it shows:
```
Dairy Milk - 360g
Tesco Finest Sea Salt & Chardonnay Vinegar Crisps 150G
2 Custard Slices
Stockwell & co Custard 385g
Stockwell & co Custard 385g
Stockwell & co Rice Pudding 400g
Stockwell & co Rice Pudding 400g
Tesco Paracetamol 500mg 16 pack
Tesco Shower Gel 300ml
Tesco Malt Wheats Cereal 750g
Tesco Malt Wheats Cereal 750g
Tesco Malt Wheats Cereal 750g
2 Garlic Baguettes 338g
4 battered white fish fillets 400g
4 battered white fish fillets 400g
Tesco Crinkle Cut oven chips 1.5Kg
```

[Return to LINQ](_LINQ.md)

[Return to Home](Home)
