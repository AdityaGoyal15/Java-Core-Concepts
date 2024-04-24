## Polymorphism

Polymorphism is a fundamental concept in object-oriented programming (OOP) that allows objects of different types to be
treated uniformly through a common interface. It enables flexibility and extensibility in software design by allowing
classes to provide different implementations of methods with the same name or signature. Polymorphism promotes code
reuse, modularity, and flexibility, making it a powerful tool for building complex software systems.

Here's a detailed explanation of polymorphism with an example:

### Example: Polymorphism in a Shape Hierarchy

Building upon the previous example (refer Inheritance.README.md) of a shape hierarchy, let's explore how polymorphism
can be applied to create a flexible and extensible system for working with shapes.

**Step 1: Define a Shape Interface or Abstract Class**

The first step in applying polymorphism is to define a common interface or abstract class that defines the common
behavior shared by all shapes. This interface or abstract class serves as the contract that shapes must adhere to.

```java
public interface Shape {
    double area();
}
```

In this example, we define a Shape interface with a single method area(), which calculates the area of a shape.
Alternatively, we can use an abstract class with abstract methods if we want to provide default implementations for some
methods.

**Step 2: Create Specific Shape Implementations**

Next, we can create concrete implementations of the Shape interface for specific types of shapes, such as circles,
rectangles, and triangles. Each shape class provides its own implementation of the area() method.

```java
public class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius; // Area of a circle
    }
}

public class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double area() {
        return width * height; // Area of a rectangle
    }
}
```

In this example, we define Circle and Rectangle classes that implement the Shape interface. Each class provides its own
implementation of the area() method to calculate the area of the specific shape.

**Step 3: Use Polymorphism to Interact with Shapes**

Finally, we can use polymorphism to interact with shapes in a flexible and generic way, treating objects of different
shape classes uniformly through their common interface.

```java
public class Main {
    public static void main(String[] args) {
        Shape circle = new Circle(5.0);
        Shape rectangle = new Rectangle(3.0, 4.0);

        System.out.println("Circle Area: " + circle.area());
        System.out.println("Rectangle Area: " + rectangle.area());
    }
}
```

In this example, we create objects of the Circle and Rectangle classes and assign them to variables of type Shape. We
then call the area() method on these objects, which is polymorphically dispatched to the appropriate implementation
based on the runtime type of the objects.

### Benefits of Polymorphism

- **Flexibility**: Polymorphism allows objects of different types to be treated uniformly through a common interface,
  enabling flexible and generic code that can work with diverse objects.
- **Extensibility**: Polymorphism promotes extensibility by allowing new subclasses to be added without modifying
  existing code. New subclasses can provide their own implementations of methods and seamlessly integrate with existing
  code.
- **Simplicity**: Polymorphism simplifies code by reducing the need for conditional logic and type checking. It
  promotes a more natural and intuitive way of expressing relationships and interactions between objects.

Overall, polymorphism is a powerful mechanism in object-oriented programming that enables flexibility, extensibility,
and simplicity in software design. By treating objects of different types uniformly through common interfaces,
polymorphism promotes code reuse, modularity, and maintainability, making it an essential concept in OOP.

