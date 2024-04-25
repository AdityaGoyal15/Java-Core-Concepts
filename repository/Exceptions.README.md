## Exceptions in Java

Exceptions in Java are objects that represent exceptional conditions that occur during the execution of a program. They
can occur due to various reasons such as runtime errors, logical errors, or exceptional circumstances. Java provides a
robust exception handling mechanism to deal with such situations.

Exceptions are primarily used to:

- **Signal and Propagate Errors**: When an exceptional condition occurs, an exception object is created and thrown. This
  signals that something unexpected has happened, and the exception is propagated up the call stack until it is caught
  and handled, or until it reaches the top-level method, resulting in program termination.
- **Separate Error-Handling Logic**: Exception handling allows you to separate error-handling logic from normal program
  flow. This makes the code cleaner, more maintainable, and easier to understand.
- **Graceful Error Recovery**: Exception handling allows you to gracefully recover from errors by providing mechanisms
  to catch, handle, and potentially recover from exceptional conditions.

### Exception Hierarchy

Java's exception hierarchy is organized in a tree-like structure, with the root class Throwable at the top. The two main
categories of exceptions are:

- **Checked Exceptions**: These are exceptions that are checked at compile time. They are subclasses of Exception but
  not subclasses of RuntimeException. Examples include IOException, SQLException, etc.
- **Unchecked Exceptions (Runtime Exceptions)**: These are exceptions that are not checked at compile time. They are
  subclasses of RuntimeException. Examples include NullPointerException, ArrayIndexOutOfBoundsException,
  ArithmeticException, etc.

Let's dive deeper into exceptions in Java, covering how to create custom exceptions, how exceptions are handled, and how
they propagate in the code.

### Creating Custom Exceptions

You can create custom exceptions by extending the Exception class or one of its subclasses. Here's an example:

```java
public class CustomException extends Exception {
    public CustomException(String message) {
        super(message);
    }
}
```

### Throwing Exceptions

You can throw an exception using the throw keyword. Here's an example of throwing a custom exception:

```java
public class MyClass {
    public void checkAge(int age) throws CustomException {
        if (age < 18) {
            throw new CustomException("Age must be 18 or above");
        }
    }
}
```

### Catching Exceptions

Exceptions can be caught and handled using try-catch blocks. Here's an example:

```java
public class Main {
    public static void main(String[] args) {
        try {
            MyClass obj = new MyClass();
            obj.checkAge(15);
        } catch (CustomException e) {
            System.err.println("Caught CustomException: " + e.getMessage());
        }
    }
}
```

### Multiple Catch Blocks

You can catch different types of exceptions using multiple catch blocks. **They are checked in order, so make sure more
specific exceptions come before more general ones**.

```java
public class Main {
    public static void main(String[] args) {
        try {
            // Code that may throw exceptions
        } catch (CustomException e) {
            // Handle CustomException
        } catch (Exception e) {
            // Handle other exceptions
        }
    }
}
```

### Finally Block

You can use a finally block to execute cleanup code regardless of whether an exception occurs or not. It executes after
the try block and any matching catch blocks.

```java
public class Main {
    public static void main(String[] args) {
        try {
            // Code that may throw exceptions
        } catch (CustomException e) {
            // Handle CustomException
        } finally {
            // Cleanup code
        }
    }
}
```

### Exception Propagation

Exceptions propagate up the call stack until they are caught and handled or until they reach the top-level method (main
method), resulting in program termination.

```java
public class Main {
    public static void main(String[] args) {
        try {
            method1();
        } catch (CustomException e) {
            // Handle CustomException
        }
    }

    public static void method1() throws CustomException {
        method2();
    }

    public static void method2() throws CustomException {
        // Code that may throw CustomException
    }
}
```

In this example, if method2 throws a CustomException and it's not caught in method2, it propagates to method1, and if
not caught there, it propagates to main.

Exceptions in Java play a vital role in handling unexpected or exceptional conditions that may occur during program
execution. By understanding how to create, throw, catch, and handle exceptions effectively, you can ensure that your
Java programs are more robust, reliable, and maintainable.
