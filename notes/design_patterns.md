# Design Patterns

## Creational Patterns

### Factory

Allows the creation of objects without specifying their concrete classes.
NB this can also be achieved with a class accepting delegate.

```csharp

public interface IProduct
{
    string Operation();
}

// Abstract creator - 
abstract class ProdctFactory{
    public abstract IProduct CreateProduct();
}

// Concrete creators
class MugFactory : ProdctFactory{
    public override IProduct CreateProduct()
    {
        return new Mug();
    }    
}

class TeacupFactory : ProdctFactory{
    public override IProduct CreateProduct()
    {
        return new Teacup();
    }    
}
```

### Builder

Allows flexibility and higher level of granularity over the object creation process.

### Singleton


## Strategy

## Decorator

## Observer


## Facade

## Repository

[8 Design Patterns](https://www.youtube.com/watch?v=tAuRQs_d9F8)

[Sopme stuff here...](https://refactoring.guru/design-patterns/csharp)

[Ultra Simple Explanations](https://github.com/kamranahmedse/design-patterns-for-humans)