## Object in OOP

In object-oriented programming (OOP), an object is a fundamental building block that represents a real-world entity or
concept. An object encapsulates data (attributes or properties) and behaviors (methods or functions) that operate on the
data. Objects are instances of classes, which serve as blueprints or templates for creating objects with similar
characteristics and behaviors.

### Characteristics of Objects

- **State**: The state of an object refers to the current values of its attributes or properties. These values define
  the object's identity and determine its behavior.
- **Behavior**: The behavior of an object is defined by the methods or functions associated with it. These methods
  operate on the object's state and perform specific actions or computations.
- **Identity**: Each object has a unique identity that distinguishes it from other objects. This identity is typically
  represented by a memory address in programming languages.

### Example

```java
public class Car {
    // Attributes or properties
    private String brand;
    private String model;
    private int year;

    // Constructor
    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }

    // Method to display information about the car
    public void displayInfo() {
        System.out.println("Brand: " + brand);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
    }
}
```

In this example, Car is a class that represents a car entity. An object of the Car class would encapsulate specific data
such as the brand, model, and year of manufacture. For example:

```java
public class Main {
    public static void main(String[] args) {
        // Creating objects of the Car class
        Car car1 = new Car("Toyota", "Corolla", 2020);
        Car car2 = new Car("Honda", "Civic", 2019);

        // Invoking methods on objects
        car1.displayInfo(); // Display information about car1
        car2.displayInfo(); // Display information about car2
    }
}
```

In this example, car1 and car2 are objects of the Car class, each representing a specific car entity with its own brand,
model, and year attributes. Objects allow us to model and manipulate real-world entities in our programs, making OOP a
powerful paradigm for software development.

