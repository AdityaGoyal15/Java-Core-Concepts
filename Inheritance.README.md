## Inheritance

Inheritance is a key concept in object-oriented programming (OOP) that allows a class (subclass or derived class) to
inherit properties and behavior from another class (superclass or base class). It promotes code reuse and supports the
creation of hierarchies of classes with specialized functionality. Inheritance enables the subclass to inherit fields
and methods from the superclass and to extend or override them as needed.

Here's a detailed explanation of inheritance with an example:

### Example: Inheritance in a Shape Hierarchy

Suppose we are developing a software system to model different geometric shapes, such as circles, rectangles, and
triangles. We want to represent these shapes using object-oriented principles, with a focus on inheritance to promote
code reuse and modularity.

**Step 1: Define a Shape Class (Superclass)**

The first step in inheritance is to define a superclass that contains common properties and behavior shared by all
shapes. This class serves as the base for other shape classes.

```java
public class Shape {
    protected String color;

    public Shape(String color) {
        this.color = color;
    }

    public void setColor(String color) {
        this.color = color;
    }

    public String getColor() {
        return color;
    }

    public double area() {
        return 0.0; // Default implementation for area
    }
}
```

In this example, we define a Shape class with a color field and methods for setting and getting the color of the shape.
We also provide a default implementation for the area() method, which returns 0.0.

**Step 2: Create Specific Shape Classes (Subclasses)**

Next, we can create specific shape classes by extending the Shape class and providing implementations for their unique
properties and behavior.

```java
public class Circle extends Shape {
    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius; // Area of a circle
    }
}

public class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(String color, double width, double height) {
        super(color);
        this.width = width;
        this.height = height;
    }

    @Override
    public double area() {
        return width * height; // Area of a rectangle
    }
}
```

In this example, we define Circle and Rectangle classes that extend the Shape class. Each subclass provides its own
implementations for the area() method, which calculates the area of the specific shape.

**Step 3: Use Inheritance to Interact with Shapes**

Finally, we can use inheritance to interact with shapes in a generic way, treating objects of different shape classes
uniformly through their common superclass.

```java
public class Main {
    public static void main(String[] args) {
        Shape circle = new Circle("red", 5.0);
        Shape rectangle = new Rectangle("blue", 3.0, 4.0);

        System.out.println("Circle Area: " + circle.area());
        System.out.println("Rectangle Area: " + rectangle.area());
    }
}
```

In this example, we create objects of the Circle and Rectangle classes and assign them to variables of type Shape. We
then call the area() method on these objects, which is polymorphically dispatched to the appropriate implementation
based on the runtime type of the objects.

### Benefits of Inheritance

- **Code Reuse**: Inheritance allows common functionality to be shared among classes, reducing code duplication and
  promoting modularity and maintainability.
- **Hierarchical Organization**: Inheritance supports the creation of class hierarchies, where classes can be organized
  in a hierarchical structure based on their relationships and levels of specialization.
- **Polymorphism**: Inheritance enables polymorphic behavior, allowing objects of different subclasses to be treated
  uniformly through a common superclass interface.

Overall, inheritance is a powerful mechanism in object-oriented programming that enables code reuse, modularity, and
polymorphism. It facilitates the creation of modular, extensible, and maintainable software systems by organizing
classes into hierarchical structures and promoting the reuse of common functionality across related classes.