## Method Overloading & Overriding

Method overloading and method overriding are both examples of polymorphism in object-oriented programming.

### Method Overloading

Method overloading occurs when a class has multiple methods with the same name but different parameter lists. In Java,
the compiler selects the appropriate method to call based on the number and types of arguments passed to the method.

```java
public class Example {
    public void doSomething(int x) {
        System.out.println("Method with int parameter: " + x);
    }

    public void doSomething(double y) {
        System.out.println("Method with double parameter: " + y);
    }
}
```

In this example, the doSomething method is overloaded with two versions—one that takes an int parameter and another that
takes a double parameter. The appropriate version of the method is selected at compile-time based on the argument
passed.

When working with method overloading in Java, there are specific rules and considerations to keep in mind to ensure
correct behavior and maintain code clarity. Here are the associated rules:

- **Method Signature**: Overloaded methods must have the same name but different parameter lists. The parameter lists
  can differ in the number of parameters, the types of parameters, or both.
- **Return Type**: The return type of overloaded methods can be the same or different, but it alone is not sufficient to
  distinguish between overloaded methods. Overloaded methods must have different parameter lists.
- **Access Modifier**: Overloaded methods can have different access modifiers (e.g., public, private, protected,
  package-private), but the method name and parameter lists must match exactly.
- **Exceptions**: Overloaded methods can declare different checked or unchecked exceptions, or even no exceptions at
  all. However, the parameter lists must still differ to distinguish between overloaded methods.
- **Varargs**: Overloaded methods can have varargs parameters, but the varargs parameter must be the last parameter in
  the parameter list.

### Method Overriding

Method overriding occurs when a subclass provides a specific implementation of a method that is already defined in its
superclass. It allows a subclass to provide its own implementation of a method inherited from its superclass.

```java
public class Animal {
    public void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Dog barks");
    }
}
```

In this example, the Dog class overrides the makeSound method defined in its superclass Animal. When a Dog object calls
the makeSound method, the overridden version in the Dog class is invoked instead of the one in the Animal class.

When working with method overriding in Java, there are specific rules and considerations to keep in mind to ensure
correct behavior and maintain code clarity. Here are the associated rules:

- **Method Signature**: Overridden methods must have the same name, return type, and parameter list (including the order
  and types of parameters) as the method being overridden.
- **Access Modifier**: Overriding methods cannot have a more restrictive access modifier than the overridden method.
  However, they can have a less restrictive access modifier or the same access modifier.
- **Exceptions**: Overriding methods can declare the same exceptions as the overridden method or a subset of the
  exceptions declared by the overridden method. They cannot declare new or broader checked exceptions.
- **Final and Static Methods**: Final methods cannot be overridden, as they are already sealed in their implementation.
  Similarly, static methods cannot be overridden; they can only be hidden (not overridden) in subclasses.
- **Super Keyword**: Overriding methods can use the super keyword to invoke the superclass version of the overridden
  method.
- **Object Class Methods**: Methods inherited from the Object class (e.g., toString(), equals(), hashCode()) can be
  overridden in subclasses to provide custom behavior.

