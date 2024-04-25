## Serialization

Serialization in Java refers to the process of converting an object into a byte stream, which can be stored in a file,
sent over a network, or persisted in a database. Conversely, deserialization is the process of reconstructing an object
from its serialized form. Serialization is commonly used for data persistence, inter-process communication, and
distributed computing. Let's explore serialization concepts with an example:

```java
import java.io.*;

// Serializable class
class Person implements Serializable {
    private static final long serialVersionUID = 1L;
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person [name=" + name + ", age=" + age + "]";
    }
}

public class SerializationExample {
    public static void main(String[] args) {
        // Serialize object
        try (ObjectOutputStream outputStream = new ObjectOutputStream(new FileOutputStream("person.ser"))) {
            Person person = new Person("John", 30);
            outputStream.writeObject(person);
            System.out.println("Serialization complete");
        } catch (IOException e) {
            e.printStackTrace();
        }

        // Deserialize object
        try (ObjectInputStream inputStream = new ObjectInputStream(new FileInputStream("person.ser"))) {
            Person person = (Person) inputStream.readObject();
            System.out.println("Deserialization complete");
            System.out.println("Deserialized object: " + person);
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
```

In this example:

- We have a Person class that implements the Serializable interface. This indicates that instances of this class can
  be serialized.
- We create an instance of the Person class and serialize it by writing it to a file named "person.ser" using an
  ObjectOutputStream.
- We then deserialize the object by reading it from the file using an ObjectInputStream.

### Important Points

- The Serializable interface is a marker interface, meaning it does not contain any methods. It simply indicates that
  the class is serializable.
- All fields of a serializable class are automatically serialized unless marked as transient.
- The serialVersionUID field is used to ensure compatibility between the serialized and deserialized objects, helping
  to prevent class version mismatches.
- It is recommended to explicitly define the serialVersionUID to control serialization versioning.

### When to Use Serialization

- Storing object states persistently (e.g., saving user preferences).
- Passing objects between different parts of an application or different applications.
- Communicating objects over a network in distributed systems.

Serialization is a powerful mechanism in Java for object persistence and communication. However, it should be used
judiciously, considering factors such as performance, security, and versioning requirements.