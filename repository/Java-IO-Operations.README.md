## Java I/O Operations

Java I/O (Input/Output) operations and framework provide a way to perform input and output operations in Java, allowing
you to read data from various sources such as files, streams, and network sockets, as well as write data to these
sources. Java provides a rich set of classes and interfaces in the java.io and java.nio packages for performing I/O
operations. Here's an overview of key concepts and classes:

### Byte Streams and Character Streams

- **Byte Streams**: Byte streams provide a way to read and write data one byte at a time. They are suitable for reading
  and writing binary data, such as images, audio files, etc. Examples include InputStream, OutputStream,
  FileInputStream, FileOutputStream, etc.
- **Character Streams**: Character streams provide a way to read and write character data, handling character encoding
  and decoding automatically. They are suitable for reading and writing text-based data. Examples include Reader,
  Writer, FileReader, FileWriter, etc.

### File I/O

- **File Class**: The File class represents a file or directory path in the file system. It provides methods for
  creating, deleting, renaming, and querying file attributes.
- **FileInputStream/FileOutputStream**: These classes allow reading and writing data to files in the file system as byte
  streams.
- **FileReader/FileWriter**: These classes allow reading and writing data to files in the file system as character
  streams.

### Buffered I/O

- **BufferedInputStream/BufferedOutputStream**: These classes provide buffering functionality for byte streams,
  improving I/O performance by reducing the number of system calls.
- **BufferedReader/BufferedWriter**: These classes provide buffering functionality for character streams, improving I/O
  performance by reducing the number of system calls.

### NIO (New I/O) API

- **Channels**: The java.nio.channels package provides support for channels, which represent connections to I/O devices
  such as files and sockets. Channels provide better support for asynchronous I/O operations.
- **Buffers**: The java.nio package provides buffer classes such as ByteBuffer, CharBuffer, etc., for reading and
  writing data efficiently.
- **Selectors**: The Selector class allows multiplexed I/O operations, enabling efficient handling of multiple channels
  in a single thread.

Let's have a look at following examples to see how we can perform read/write operations in Java I/O framework:

**Reading and Writing Text Files**

```java
import java.io.*;

public class Main {
    public static void main(String[] args) {
        try {
            // Writing to a text file
            FileWriter writer = new FileWriter("output.txt");
            writer.write("Hello, World!\n");
            writer.close();

            // Reading from a text file
            FileReader reader = new FileReader("output.txt");
            BufferedReader bufferedReader = new BufferedReader(reader);
            String line;
            while ((line = bufferedReader.readLine()) != null) {
                System.out.println(line);
            }
            bufferedReader.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

In this example:

- We create a FileWriter to write data to a text file named "output.txt".
- We create a FileReader and wrap it with a BufferedReader to read data from the same file.
- We read each line from the file and print it to the console.

**Reading and Writing Binary Files**

```java
import java.io.*;

public class Main {
    public static void main(String[] args) {
        try {
            // Writing to a binary file
            FileOutputStream outputStream = new FileOutputStream("data.bin");
            DataOutputStream dataOutputStream = new DataOutputStream(outputStream);
            dataOutputStream.writeInt(42);
            dataOutputStream.close();

            // Reading from a binary file
            FileInputStream inputStream = new FileInputStream("data.bin");
            DataInputStream dataInputStream = new DataInputStream(inputStream);
            int value = dataInputStream.readInt();
            System.out.println("Value: " + value);
            dataInputStream.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

In this example:

- We create a FileOutputStream and wrap it with a DataOutputStream to write binary data to a file named "data.bin".
- We create a FileInputStream and wrap it with a DataInputStream to read binary data from the same file.
- We read an integer value from the file and print it to the console.

**Using Try-With-Resources**

```java
import java.io.*;

public class Main {
    public static void main(String[] args) {
        try (BufferedReader reader = new BufferedReader(new FileReader("input.txt"));
             BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"))) {
            String line;
            while ((line = reader.readLine()) != null) {
                writer.write(line);
                writer.newLine();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

In this example:

- We use try-with-resources to automatically close the resources (Reader and Writer) after the try block finishes
  executing.
- We read from an input text file named "input.txt" and write its contents to an output text file named "output.txt".

**File and Directory Operations**

```java
import java.io.*;

public class Main {
    public static void main(String[] args) {
        File directory = new File("my_directory");
        if (!directory.exists()) {
            if (directory.mkdir()) {
                System.out.println("Directory created successfully");
            } else {
                System.out.println("Failed to create directory");
            }
        } else {
            System.out.println("Directory already exists");
        }
    }
}
```

In this example:

- We create a File object representing a directory named "my_directory".
- We check if the directory exists using the exists() method.
- If the directory does not exist, we create it using the mkdir() method.

These examples cover some basic Java I/O operations and framework concepts, including reading and writing text and
binary files, using try-with-resources, and performing file and directory operations. Understanding these concepts is
essential for working with I/O in Java effectively.