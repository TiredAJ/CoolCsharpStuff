---
tags:
  - Regions
  - XML_Comments
---
Regions are a really simple, really easy way to tidy up code. It allows you to define collapsible sections. Our _CargoContainer_ class from earlier could do with some regions:

```C#
public class CargoContainer<T>
{
    #region Member Variables
    public string ID { get; set; } = "";
    public Address Destination { get; set; }
    private T? Contents;
    private List<(DateTime TimeStamp, string Action)> Log;
    #endregion

    public CargoContainer(string _ID, Address _Dest)
    {
        ID = _ID;
        Destination = _Dest;
        Log = new List<(DateTime TimeStamp, string Action)>();
        Contents = default;
    }
	#region Member Functions
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
    public List<(DateTime TimeStamp, string Action)> GetLog()
    { return Log; }
    #endregion
}
```

The above can be collapsed into:
![[Pasted image 20231121220155.png]]

It’s up to you where you define regions. I like collecting member variables into one and grouping related functions together:
![[Pasted image 20231121220227.png | 400]]

The example also gives another peek at the next bit, which is XML comments.

A really useful way to comment code is using XML comments for class and functions. Very simply, you use three `///` instead of two `//`. (potentially IDE dependent), this should auto-generate a template for your class or function:
```C#
/// <summary>
/// 
/// </summary>
/// <param name="_Cargo"></param>
public void EncloseCargo(T _Cargo)
{
    Contents = _Cargo;
    Log.Add((DateTime.Now, "Cargo Encased"));
}
```

Within this, you can specify what the function does, what its parameters are, what it returns and what exceptions it can throw. For our _EncloseCargo()_ function, we can write:
```C#
/// <summary>
/// Encloses the cargo into the container
/// </summary>
/// <param name="_Cargo">The cargo to enclose</param>
public void EncloseCargo(T _Cargo)
{
    Contents = _Cargo;
    Log.Add((DateTime.Now, "Cargo Encased"));
}
```
*It could be commented better, but just for a demo, it works.*

But now it’s commented, we can see the best part. When we go to use this function, we’ll be able to see our comment:
![[Pasted image 20231121220448.png | 700]]
![[Pasted image 20231121220505.png | 700]]

With VS, it's a bit finnicky.

There’s also a bunch of [tags you can use](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/recommended-tags) to detail your comments better.

[Return to Home](Home)
