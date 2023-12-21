---
tags:
  - TernaryOperator
---
`not sure if this'll stay in this folder`
Need a quick and short if? Give the ternary operator `?:` a go:
```C#
static void Main(string[] args)
{
    float Temperature = 0.0f;

    Console.WriteLine("What is the temperature today?");
    float.TryParse(Console.ReadLine().Replace("°C", ""), out Temperature);

    Console.WriteLine(Temperature > 23 ? "Bloody hot out" : "Ah, probably nice");
}
```
The program asks for the temperature from the user (assumed correct units are used or just the value is inputted). The input is parsed into a float and the ternary operator either returns the strings "Bloody hot out" if it's above 23°C or "Ah, probably nice". Either of which is directly passed to `WriteLine()`.
