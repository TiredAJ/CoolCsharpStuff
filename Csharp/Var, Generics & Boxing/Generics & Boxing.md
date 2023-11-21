---
tags:
  - Generics
  - Boxing
---
Generics are like templates in C++, they allow you to specify the type for a function later. The _Print()_ function from [LINQ](_LINQ) uses generics:
```C#
static void Print<T>(List<T> _L)
{
    foreach (var I in _L)
    {Console.WriteLine(I.ToString());}
}
```
The `<T>` after the function name specifies that the function uses generics and that anything labelled T could be of any type. This is used for the function’s single parameter: A list holding elements of type T.

Usually when you want to call a generic function you need to specify what type it should be using:
```C#
Print<Item>(ShoppingBasket);
```
VS might grey it out because sometimes the compiler can work out what type it should be. 

It’s not only functions that can use generics, classes can too. For example, say you needed to emulate a smart shipping container:
```C#
public class CargoContainer<T>
{
    public string ID { get; set; } = "";
    public Address Destination { get; set; }
    private T? Contents;
    private List<(DateTime TimeStamp, string Action)> Log;

    public CargoContainer(string _ID, Address _Dest)
    {
        ID = _ID;
        Destination = _Dest;
        Log = new List<(DateTime TimeStamp, string Action)>();
        Contents = default;
    }
    public void EncloseCargo(T _Cargo)
    {
        Contents = _Cargo;
        Log.Add((DateTime.Now, "Cargo Encased"));
    }
    public T? AccessCargo()
    {
        Log.Add((DateTime.Now, "Cargo Accessed"));
        return Contents;
    }
    public List<(DateTime TimeStamp, string Action)> GetLog() => Log;
}
```

_CargoContainer_ can hold any object as long as it’s defined at creation. For example, we can put some precious items into a container (using *Item* class from [LINQ](_LINQ)):
```C#
Item Chocolate = new Item("Dairy Milk - 360g", 3.5f);

CargoContainer<Item> ChocContainer = new CargoContainer<Item>("929a929b", Destination);

ChocContainer.EncloseCargo(Chocolate);
```
 
With the `<Item>`, we're defining what `T` will be. In this case, it's of type `Item`.

The container can then be loaded onto the cargo ship and shipped straight to my house:
```C#
CargoShip.LoadContainer<Item>(ChocContainer);
```

_CargoContainer_ could also make use of _boxing_. This is where an object is casted to an _object_. For our CargoContainer class, we could keep aspects of generics to save the person receiving the cargo needing to recast the object, or take out generics completely:

## Some Generics
(Unchanged sections have been commented out)
```C#
public class CargoContainer<T>
{
    /*Member Variables*/
	private object? Contents;

    public CargoContainer(string _ID, Address _Dest)
    {/**/}
    public void EncloseCargo(T _Cargo)
    {/**/}
    
    public T? AccessCargo()
    {
        Log.Add((DateTime.Now, "Cargo Accessed"));
        return (T?)Contents;
    }
    
    public List<(DateTime TimeStamp, string Action)> GetLog() => Log;
}
```

So now instead of Contents being of type T (nullable), it’s now of type _object_ (nullable). _AccessCargo()_ still returns a nullable T because it's contents are casted to (nullable) T on return.

## No Generics
Again, the recipient would need to cast the object back to it’s intended type on reception.
(Unchanged sections have been commented out)
```C#
public class CargoContainer
{
    /*Member Variables*/
	private object? Contents;

    public CargoContainer(string _ID, Address _Dest)
    {/**/}
    public void EncloseCargo(T _Cargo)
    {/**/}
    
    public object? AccessCargo()
    {
        Log.Add((DateTime.Now, "Cargo Accessed"));
        return Contents;
    }
    
    public List<(DateTime TimeStamp, string Action)> GetLog() => Log;
}
```

Here, generics are completely done away with.
```C#
CargoContainer<Item> ChocContainer = new CargoContainer<Item>("929a929b", Destination);

ChocContainer.EncloseCargo(Chocolate);

CargoShip.LoadContainer<Item>(ChocContainer);

Console.WriteLine(ChocContainer.AccessCargo());
```

While _Console.WriteLine()_ doesn’t need to recast for it to call the right _ToString()_:
```
Dairy Milk - 360g 	£3.50
```
![[Pasted image 20231121214248.png]]

To access any of the contents’ properties, it needs to be casted:
![[Pasted image 20231121214319.png | 600]]

`Contents.Name` is in red squiggly because it needs to be *recasted*. The green squiggly is because it’s converting a nullable to a non-nullable type, and there’s a chance it’ll throw an error if _Contents_ is null. 

> [!info] The Docs warn that [boxing is an expensive operation](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/types/boxing-and-unboxing#performance);

[Check out *Var*](Var)

[Return to Home](Home)