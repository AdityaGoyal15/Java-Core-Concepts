## Static Keyword

In Java, the static keyword is used to declare members (fields, methods, and nested classes) that belong to the class
itself rather than to individual instances (objects) of the class. When a member is declared as static, it is shared
among all instances of the class and can be accessed using the class name, without needing to create an instance of the
class.

Here's an explanation of the static keyword and its associated rules with examples:

### Static Fields

```java
public class Example {
    private static int count; // Static field

    public Example() {
        count++; // Increment count each time a new instance is created
    }

    public static int getCount() {
        return count; // Access static field
    }
}
```

In this example, the count field is declared as static. This means that there is only one count variable shared among
all instances of the Example class, and it is accessed using the class name (Example.count). Each time a new instance of
Example is created, the count is incremented.

### Static Methods

```java
public class MathUtils {
    public static int add(int a, int b) {
        return a + b; // Static method
    }
}
```

In this example, the add method is declared as static. This means that the add method belongs to the MathUtils class
itself rather than to instances of the class. It can be called using the class name (MathUtils.add(5, 3)) without
needing to create an instance of MathUtils.

### Static Blocks

```java
public class InitializationExample {
    static {
        // Static initialization block
        System.out.println("Static block executed");
    }
}
```

In this example, a static initialization block is used to initialize static fields or perform other static
initialization tasks. Static initialization blocks are executed when the class is loaded into memory, typically before
any instances of the class are created.

### Associated Rules

- **Static Members**: Static members belong to the class itself rather than to individual instances of the class. They
  are shared among all instances of the class and can be accessed using the class name.
- **Accessing Static Members**: Static members can be accessed directly using the class name (ClassName.member) or
  through an instance of the class (instance.member). However, accessing static members through an instance is
  discouraged and may lead to confusion.
- **Initialization**: Static fields are initialized when the class is loaded into memory, and static initialization
  blocks are executed in the order they appear in the class file.
- **Static Methods**: Static methods cannot access instance variables or instance methods directly, as they are not
  associated with any particular instance. They can only access other static members directly.
- **Static vs. Instance Context**: Static members operate in a class-level context, whereas instance members operate in
  an object-level context. Static members are initialized once when the class is loaded, whereas instance members are
  initialized each time an instance of the class is created.

By understanding these rules and using the static keyword appropriately, you can leverage static members effectively in
your Java programs to share data and behavior among instances of a class and perform class-level initialization tasks.