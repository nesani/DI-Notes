# Decorator
Decorator is a structural design pattern that lets you attach new behaviors to objects by placing these objects inside special wrapper objects that contain the behaviors.

![Decorator Solution](../../Images/Design-Patterns/Decrator-Solution.png)

**Use the Decorator pattern when you need to be able to assign extra behaviors to objects at runtime without breaking the code that uses these objects.**

**Use the pattern when it’s awkward or not possible to extend an object’s behavior using inheritance.**

**Many programming languages have the final keyword that can be used to prevent further extension of a class. For a final class, the only way to reuse the existing behavior would be to wrap the class with your own wrapper, using the Decorator patter**

## Pros

- You can extend an object’s behavior without making a new subclass.
- You can add or remove responsibilities from an object at runtime.
- You can combine several behaviors by wrapping an object into multiple decorators
- Single Responsibility Principle. You can divide a monolithic class that implements many possible variants of behavior into several smaller classes

# Cons
- It’s hard to remove a specific wrapper from the wrappers stack.
- It’s hard to implement a decorator in such a way that its behavior doesn’t depend on the order in the decorators stack.
- The initial configuration code of layers might look pretty ugly.


Detailed example: "https://refactoring.guru/design-patterns/decorator"

