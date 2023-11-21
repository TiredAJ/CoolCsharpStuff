---
tags:
  - LINQ
---
Is good for filtering through a collection and getting a collection of elements that match your query. For example, if I wanted all the items under £1.00:
```C#
List<Item> Cheap = ShoppingBasket.Where(X => X.Price < 1.0f).ToList();
```
Inside the (brackets) is the “predicate”, this is the query that is applied against each element (represented by _X_). So the query above checks if `X.Price` is less than 1.0f (£1). If the cheap list was put into the print function, it’ll output:
```
Stockwell & co Custard 385g     £0.58
Stockwell & co Custard 385g     £0.58
Stockwell & co Rice Pudding 400g        £0.25
Stockwell & co Rice Pudding 400g        £0.25
Tesco Paracetamol 500mg 16 pack £0.39
Tesco Shower Gel 300ml  £0.35
Tesco Malt Wheats Cereal 750g   £0.95
Tesco Malt Wheats Cereal 750g   £0.95
Tesco Malt Wheats Cereal 750g   £0.95
2 Garlic Baguettes 338g £0.89
```

[Return to LINQ](_LINQ.md)

[Return to Home](Home)
