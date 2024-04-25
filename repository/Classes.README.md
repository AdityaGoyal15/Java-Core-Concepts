## Classes in Java

In Java, a class is a blueprint or template for creating objects. It defines the structure and behavior of objects of
that type. Here's a breakdown of what classes do and how they work:

- **Encapsulation**: Classes encapsulate data (attributes) and methods (functions) that operate on that data. This
  means you can bundle related data and methods together in a single unit.
- **Abstraction**: Classes allow you to create abstract data types. They hide the complexity of the underlying
  implementation and expose only the necessary details to the outside world.
- **Inheritance**: Classes support inheritance, which is a mechanism where a new class can inherit properties and
  behaviors from an existing class. This promotes code reusability and helps in creating a hierarchical structure.
- **Polymorphism**: Classes support polymorphism, which means that objects of different classes can be treated as
  objects of a common superclass. This allows for more flexible and modular code.

Here's a simple example of a Java class:

```java
public class Car {
    // Attributes
    String brand;
    String model;
    int year;

    // Constructor
    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }

    // Method
    public void start() {
        System.out.println("The " + year + " " + brand + " " + model + " is starting.");
    }
}
```

In this example, Car is a class that represents a car object. It has attributes like brand, model, and year, a
constructor to initialize those attributes when creating a Car object, and a method start() to simulate starting the
car.

Classes are fundamental to object-oriented programming (OOP) in Java and are used extensively to organize and structure
code.