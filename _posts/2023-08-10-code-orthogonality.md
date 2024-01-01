---
layout: single
title:  "Mindful development: code orthogonality"
date:   2023-08-15 20:00:00 +0100
categories: mindful coding unity
header:
  overlay_image: /assets/images/posts/orthogonality.webp
  overlay_filter: 0.6 # same as adding an opacity of 0.5 to a black background
  teaser: /assets/images/posts/orthogonality.webp
---

Today's topic is one many of us might have come across but haven't dived deeply into: Code Orthogonality. This concept, popularised by the book [The Pragmatic Programmer: From Journeyman to Master](https://en.wikipedia.org/wiki/The_Pragmatic_Programmer), is one way to create robust, efficient and maintainable code.

# What is Code Orthogonality?

The term 'Orthogonal' originates from mathematics, describing concepts that are independent of each other. When translated into software, orthogonality implies that components or functions within your software can change independently without causing a ripple effect of changes in other parts of your system. 

You may ask, "Why is this autonomy of components desirable?" Imagine the complexity and frustration when changing a single feature affects other unrelated features of your application. For example, if I change the players movement behaviour, I wouldn’t expect this to impact how the player is rendered. This is what code orthogonality intends to avoid. 

# Advantages

1. Simplicity: Each part of your system deals with a single responsibility and does not interfere with other components. This makes understanding, implementing and testing each part simpler. 

2. Efficiency: Development becomes more efficient as changes and updates do not cause cascading modifications. Separate teams can work on different parts without running into risks of breaking each other's code. If you’re working on component A, you don’t need to fear changes that another developer is making in component B.

3. Robustness: The effects of a bug are confined to a specific component, which reduces the potential of it wreaking havoc in your system. It’s like a little bug cage. Downside is that it’s harder to blame other developers when you break a component ;) 

# Tips 

1. Embrace Modularity: Try to ensure that each component of your system, be it a function, class, or module, has a single well-defined role.

2. Limit Interaction: Reduce the interaction between components to the bare minimum. This can be achieved by using well-defined interfaces and data encapsulation.

3. DRY Principle: ‘Don’t Repeat Yourself’ is another important aspect of maintainable code. Duplication increases the chances of making changes in multiple places, thus reducing orthogonality.

1. Dependency Management: Aim to minimise dependencies among components. Avoiding unnecessary dependencies helps improve orthogonality.

1.  Regular Refactoring: Keep refining and simplifying your code. 

# Examples
To help you picture this in practice, below are several examples of Code Orthogonality in Unity C#.

## Example 1: using Unity’s Entity Component System

The ECS pattern in Unity inherently promotes Code Orthogonality as each behaviour is a separate system and works independently. For example, if you have a “MovementSystem” and a “RenderSystem”, they won’t interfere with each other. The MovementSystem purely handles the logic for movement, and the RenderSystem only takes care of rendering the entities. They can function and be modified independently of each other. 

```csharp
class MovementSystem : ComponentSystem
{
    protected override void OnUpdate()
    {
        Entities.ForEach((ref Position position, ref Velocity velocity) =>
        {
            position.Value += velocity.Value * Time.deltaTime;
        });
    }
}

class RenderSystem : ComponentSystem
{
    protected override void OnUpdate()
    {
        Entities.ForEach((ref Position position, ref SpriteRenderer spriteRenderer) =>
        {
            spriteRenderer.transform.position = position.Value;
        });
    }
}
```

# Example 2: MonoBehaviour
Say we have a class `Player`, which has a weapon and is able to move. We can seperate this functionality into discrete classes:

```csharp
public class Player : MonoBehaviour
{
    private PlayerMovement playerMovement;
    private Weapon weapon;

    private void Awake()
    {
        playerMovement = GetComponent<PlayerMovement>();
        weapon = GetComponent<Weapon>();
    }

    private void Update()
    {
        playerMovement.Move();
        weapon.Fire();
    }
}

public class PlayerMovement : MonoBehaviour
{
    public void Move()
    {
        // Logic to move player
    }
}

public class Weapon : MonoBehaviour
{
    public void Fire()
    {
        // Logic to fire weapon
    }
}
```
In this example, `PlayerMovement` and `Weapon` classes operate independently of the `Player` class.

# Example 3: using Interfaces

We can also take advantage of C# Interfaces to separate concerns:

```csharp
public interface IPlayerMovement
{
    void Move();
}

public class PlayerMovement : IPlayerMovement
{
    public void Move()
    {
        // Movement Code
    }
}

public interface IWeapon
{
    void Fire();
}

public class Gun : IWeapon
{
    public void Fire()
    {
        // Shoot code
    }
}

public class Player : MonoBehaviour
{
    private IPlayerMovement playerMovement = new PlayerMovement();
    private IWeapon weapon = new Gun();

    private void Update()
    {
        playerMovement.Move();
        weapon.Fire();
    }
}
```
If you want to modify how the player shoots, you just need to create a new class that inherits from IWeapon and implement the functionality in that class.

# Sign off


Of course, code orthogonality is not a new trend. It is a strong principle that has its roots in sound software engineering practice. While it may not always be easy to maintain perfect orthogonality (unlike in these simple examples, production code can get complex very quickly), the closer we get to it, the more maintainable, robust, and efficient our software becomes. Have a mindful day!
