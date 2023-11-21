---
tags:
  - LINQ
  - Dictionaries
---
Say I wanted to convert the list of items into a dictionary where the name is the key and the price is the value. To do this I can:
```C#
Dictionary<string, float> BasketDict = ShoppingBasket
	.DistinctBy(X => X.Name)
	.ToDictionary(X => X.Name, Y => Y.Price);
```

```
[Dairy Milk - 360g]: £3.50
[Tesco Finest Sea Salt & Chardonnay Vinegar Crisps 150G]: £1.35
[2 Custard Slices]: £1.65
[Stockwell & co Custard 385g]: £0.58
[Stockwell & co Rice Pudding 400g]: £0.25
[Tesco Paracetamol 500mg 16 pack]: £0.39
[Tesco Shower Gel 300ml]: £0.35
[Tesco Malt Wheats Cereal 750g]: £0.95
[2 Garlic Baguettes 338g]: £0.89
[4 battered white fish fillets 400g]: £2.00
[Tesco Crinkle Cut oven chips 1.5Kg]: £2.50
```

[Return to LINQ](_LINQ)

[Return to Home](Home)
