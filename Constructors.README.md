## Constructors

In Java, constructors are special methods used for initializing objects of a class. They are invoked automatically when
an object is created using the new keyword. Constructors have the same name as the class and do not have a return type,
not even void. Let's explore constructors and related concepts in Java:

### Default Constructor

If a class does not explicitly define any constructors, Java provides a default constructor implicitly. This default
constructor has no parameters and initializes the object with default values.

```java
public class MyClass {
    // Default constructor
    public MyClass() {
        // Initialization code
    }
}
```

### Parameterized Constructor

A parameterized constructor is a constructor with parameters. It allows you to initialize the object with specific
values provided during object creation.

```java
public class Person {
    private String name;
    private int age;

    // Parameterized constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

### Constructor Overloading

Just like methods, constructors can be overloaded, which means you can define multiple constructors with different
parameter lists within the same class.

```java
public class Person {
    private String name;
    private int age;

    // Parameterized constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Overloaded constructor with only name parameter
    public Person(String name) {
        this.name = name;
        this.age = 0; // Default age
    }
}
```

### Constructor Chaining

In Java, constructors can call other constructors in the same class using this() keyword. This is known as constructor
chaining and can be used to reuse constructor logic.

```java
public class Person {
    private String name;
    private int age;

    // Parameterized constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Overloaded constructor with only name parameter
    public Person(String name) {
        this(name, 0); // Calling parameterized constructor
    }
}
```

### Initializing Instance Variables

Constructors are commonly used to initialize instance variables, ensuring that every object of the class starts with
valid initial state.

```java
public class Circle {
    private double radius;

    // Parameterized constructor to initialize radius
    public Circle(double radius) {
        this.radius = radius;
    }
}
```

### Invoking Parent Class Constructors

Inheritance allows constructors to invoke constructors of the superclass using super() keyword.

```java
public class Animal {
    private String species;

    // Parameterized constructor
    public Animal(String species) {
        this.species = species;
    }
}

public class Dog extends Animal {
    private String breed;

    // Parameterized constructor
    public Dog(String species, String breed) {
        super(species); // Invoking superclass constructor
        this.breed = breed;
    }
}
```

