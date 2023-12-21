---
tags:
  - SwitchCase
  - Enums
---
Switch statements are *awesome*

```C#
static void Main(string[] args)
{
    do
    {
        Console.Clear();
        Console.WriteLine("Where would you like to go?");
        Console.WriteLine("[e]xit, [d]isplay board, [h]ome, [s]ettings");

        switch (Console.Read())
        {
            case 'D':
            case 'd':
                ShowPage_DisplayBoard();
                break;
            case 'E':
            case 'e':
                return;
            case 'H':
            case 'h':
                ShowPage_Home();
                break;
            case 'S':
            case 's':
                ShowPage_Settings();
                break;
            default:
                break;
        }
    } while (true);
}

private static void ShowPage_DisplayBoard()
{...}
private static void ShowPage_Home()
{...}
private static void ShowPage_Settings()
{...}
```

They evaluate their expression and executes whichever case matches. In the example above, the user is shown a simple navigation menu and prompted for an input. From that input, the program takes the user to the menu they've selected.
while you can use
```C#
switch (char.ToLower((char)Console.Read()))
```
To remove the need for a case for uppercase and lower case. It wasn't used to show how multiple cases can go to the same selection (*fall through*).

The above also shows the default case. It's statement is executed when no other cases are matched. In the example it doesn't do anything but let the loop re-run.

Further, they work great with [[Enums]]:

```C#
public enum Direction
{
    North,
    East,
    South,
    West,
    None
}

private Vector2? GetMovement(Direction _PlayerMovement)
{
    switch (_PlayerMovement)
    {
        case Direction.North:
            return new Vector2(1, 0);
        case Direction.East:
            return new Vector2(0, 1);
        case Direction.South:
            return new Vector2(-1, 0);
        case Direction.West:
            return new Vector2(0, -1);
        case Direction.None:
        default:
            return null;
    }
}
```

The above should return a vector depending on the player's input direction. The default is included when `case Direction.None:` is already there for edge cases such as:

```C#
GetMovement((Direction)22)
```


Although our expression above could've been made more elegant(?) by using a Switch *Expression* rather than *Statement*:
```C#
private Vector2? GetElegantMovement(Direction _PlayerMovement) => _PlayerMovement switch
{
    Direction.North => new Vector2(1, 0),
    Direction.East => new Vector2(0, 1),
    Direction.South => new Vector2(-1, 0),
    Direction.West => new Vector2(0, -1),
    Direction.None or _ => null,
};
```
The underscore represents the `default:` case in the previous example. the `or` operator stands in for our *fall through* we made use of earlier.

## Case Guards
Case Guards can be used when more specificity is needed for a case:
```C#
private Vector2? GetElegantMovement(Direction _PlayerMovement, bool AutoMove) => _PlayerMovement switch
{
    Direction.North => new Vector2(1, 0),
    Direction.East => new Vector2(0, 1),
    Direction.South => new Vector2(-1, 0),
    Direction.West => new Vector2(0, -1),
    Direction.None or _ when AutoMove => new Vector2(0, 0),
    Direction.None or _ when !AutoMove => null,
};
```
In the above examples, we want to know when the player's character is being moved by something other than the player (`_AutoMove`).
With this, the function will return a zero vector if the player's being moved by something in the world, null otherwise.


