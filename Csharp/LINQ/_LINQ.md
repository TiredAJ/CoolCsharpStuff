---
tags:
  - LINQ
  - Generics
---
LINQ (Language-Integrated Query) is a wide set of functions for collections that allow you to nicely sort and collect things. There’s too many to go over, so I’ll cover the main ones.

For the examples I’ll be using the _Item_ class and the `List<Item>` “ShoppingBasket”. Also the function _Print()_:
```C#
public class Item
{
	public string Name { get; set; }
	public float Price { get; set; } = 0.0f;

	public Item(string _Name, float _Price)
	{ Name = _Name; Price = _Price; }

	public override string ToString() =>
		$"{Name}\t{Price:C}";
}

private static List<Item> ShoppingBasket = new List<Item>()
{
	new Item("Dairy Milk - 360g", 3.5f),
	new Item("Tesco Finest Sea Salt & Chardonnay Vinegar Crisps 150G", 1.35f),
	new Item("2 Custard Slices", 1.65f),
	new Item("Stockwell & co Custard 385g", 0.58f),
	new Item("Stockwell & co Custard 385g", 0.58f),
	new Item("Stockwell & co Rice Pudding 400g", 0.58f),
	new Item("Stockwell & co Rice Pudding 400g", 0.58f),
	new Item("Tesco Paracetamol 500g 16 pack", 0.39f),
	new Item("Tesco Shower Gel 300ml", 0.35f),
	new Item("Tesco Malt Wheats Cereal 750g", 0.95f),
	new Item("Tesco Malt Wheats Cereal 750g", 0.95f),
	new Item("Tesco Malt Wheats Cereal 750g", 0.95f),
	new Item("2 Garlic Baguettes 338g", 0.89f),
	new Item("4 battered white fish fillets 400g", 2.0f),
	new Item("4 battered white fish fillets 400g", 2.0f),
	new Item("Tesco Crinkle Cut oven chips 1.5kg", 2.5f)
}

static void Print<T>(List<T> _L)
{
    foreach (var I in _L)
    {Console.WriteLine(I.ToString());}
}

static void Print<K,V>(Dictionary<K,V> _D)
{
    foreach (var KVP in _D)
    {Console.WriteLine($"[{KVP.Key}]: {KVP.Value:C}");}
}
```

The `<T>` will be explained in *[[Generics & Boxing]]*.

While LINQ functions are handy, at their base most are just loops, but from my understanding, a bit optimised. I personally like using them because they look nice and elegant.


>[!info]
> _X_ and _Y_ will be used to represent an element in the collection we’re operating on. Also most of these use list (ShoppingBasket to be exact) for examples, but LINQ can be applied to most collections (arrays, dictionaries etc.).

[[_LINQ]]
	├── [[Where()]]
	├── [[Select()]]
	├── [[TakeWhile()]]
	├── [[DistinctBy()]]
	├── [[ToDictionary()]]
	└── [[Combining]]

[Return to Home](Home)
