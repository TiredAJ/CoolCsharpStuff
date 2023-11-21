---
tags:
  - LINQ
---
If you want to filter out duplicates you can use _DistinctBy()_ to filter them out. _DistinctBy()_ (as opposed to _Distinct()_) allows you to define what to distinguish by, for example, if we wanted to filter out duplicate _named_ items, we can use:
```C#
List<Item> OnlyItems = ShoppingBasket.DistinctBy(X => X.Name).ToList();
```

Which gives us:
```
Dairy Milk - 360g       £3.50
Tesco Finest Sea Salt & Chardonnay Vinegar Crisps 150G  £1.35
2 Custard Slices        £1.65
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
4 battered white fish fillets 400g      £2.00
4 battered white fish fillets 400g      £2.00
Tesco Crinkle Cut oven chips 1.5Kg      £2.50
```
Devoid of duplicates.

[Return to LINQ](_LINQ.md)

[Return to Home](Home)
