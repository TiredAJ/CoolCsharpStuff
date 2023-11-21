---
tags:
  - ExtensionMethods
---
Extension methods are a way of making new functions for predefined types without needing to alter the original type. LINQ functions are [extension methods](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).

As an example, we can add a basic extension method for the string type:
```C#
public static class ExtensionMethods
{
	public static int CountLetters(this string _Str)
	{return _str.Length;}
}
```

Very simply, it returns how many characters are in the string, something that already exists but it’s a simple example.

When we have a string object, our extension method pops up:
![[Pasted image 20231121221628.png | 600]]

It also has the `(extension)` tag.

These can be very useful, especially if the type you’re using is missing useful functions. For example, I made a bunch of [extension methods](https://github.com/TiredAJ/AJGraphicsEngine/blob/main/Back/Extensions.cs) for the _Vector2_ type from _System.Numerics_:
```C#
///<summary>
/// Returns a float representing the magnitude of this vector.
///</summary>
public static float GetMagnitude(this Vector2 V2)
{return MathF.Sqrt(((float)V2.X * (float)V2.X) + ((float)V2.Y * (float)V2.Y));}
```

It can also be used for conversion (from same class):
```C#
///<summary>
/// Returns a <c>PointF</c> representing this vector.
///</summary>
public static PointF ToPointF(this Vector2 V2)
=> new PointF(V2.X, V2.Y);
```


[Return to Home](Home)
