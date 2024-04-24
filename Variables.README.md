## Variables

In Java, variables are containers that hold data and are used to store values for manipulation and reference within a
program. Variable scopes and rules determine where and how variables can be accessed within a Java program. There are
several types of variables with different scopes and rules:

- **Local Variables**:
    - **Scope**: Local variables are declared within a method, constructor, or block of code and are accessible only
      within the enclosing block where they are declared.
    - **Lifetime**: Local variables exist only within the block in which they are declared. They are created when the
      block is entered and destroyed when the block is exited.
        - **Example**:
          ``` 
          public void exampleMethod() {
            int localVar = 10; // localVar is a local variable
            System.out.println(localVar);
          }
          ```
- **Parameters**:
    - **Scope**: Parameters are variables declared in a method's parameter list and are accessible within the method
      body.
    - **Lifetime**: Parameters exist for the duration of the method invocation.
    - **Example**:
      ```
      public void exampleMethod(int param) { // param is a parameter
        System.out.println(param);
      }
      ```
- **Instance Variables (Non-static Fields)**:
    - **Scope**: Instance variables are declared within a class but outside any method, constructor, or block. They are
      associated with instances (objects) of the class and are accessible to all methods within the class.
    - **Lifetime**: Instance variables exist for the lifetime of the object to which they belong.
    - **Example**:
      ```
        public class MyClass {
          int instanceVar; // instanceVar is an instance variable
        }
      ```
- **Class Variables (Static Fields)**:
    - **Scope**: Class variables are declared with the static keyword within a class but outside any method,
      constructor, or block. They are associated with the class itself rather than with instances of the class and are
      accessible to all methods within the class and its subclasses.
    - **Lifetime**: Class variables exist for the lifetime of the program.
    - **Example**:
      ```
      public class MyClass {
        static int classVar; // classVar is a class variable
      }
      ```

### Rules:

- Local variables must be initialized before they are used.
- Instance and class variables are automatically initialized with default values if not explicitly initialized. Numeric
  types are initialized to 0, boolean types to false, and reference types to null.
- Variables cannot have the same name within the same scope.
- The scope of a variable is determined by its declaration context.
- Variables with narrower scopes can shadow variables with broader scopes.
- Variable names must follow Java's naming conventions and cannot be Java keywords.
- Access modifiers (public, private, protected) can control the visibility and accessibility of variables.

Understanding variable scopes and rules is crucial for writing clear, maintainable, and bug-free Java code. It helps
ensure proper variable usage and prevents scope-related issues such as shadowing and variable conflicts.