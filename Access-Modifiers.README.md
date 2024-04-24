In Java, access modifiers are keywords used to control the accessibility or visibility of classes, methods, and
variables. They specify how classes, methods, or variables can be accessed or used by other classes and code within the
same package or from external packages. Java provides four types of access modifiers:

- **public**: The public access modifier allows unrestricted access to the class, method, or variable from any other
  class or package. Classes, methods, or variables marked as public are accessible from anywhere.
- **protected**: The protected access modifier allows access to the class, method, or variable from within the same
  package and by subclasses (in any package). It restricts access from classes outside the package that are not
  subclasses of the class.
- **default (no modifier)**: If no access modifier is specified, the default access modifier is applied. Classes,
  methods, or variables with default access are accessible only within the same package. They are not accessible to
  classes outside the package or subclasses in other packages.
- **private**: The private access modifier restricts access to the class, method, or variable to the same class only. It
  prevents access from any other class, including subclasses and classes in the same package.