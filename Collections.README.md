## Collections in Java

The Java Collections Framework provides a comprehensive set of interfaces and classes to represent and manipulate
collections of objects. Collections offer functionalities such as adding, removing, and accessing elements, as well as
sorting, searching, and iterating over elements. Let's explore the key interfaces in the Collections API along with
examples and compare different implementations of these interfaces, including concurrent implementations:

### List Interface

The List interface represents an ordered collection of elements that allows duplicate elements.

- **ArrayList**: Implements the List interface using a dynamic array. It provides fast random access but slower
  insertion and deletion compared to LinkedList.

```java
class Main {
    public static void main(String[] args) {
        List<String> arrayList = new ArrayList<>();
        arrayList.add("Apple");
        arrayList.add("Banana");
        arrayList.add("Orange");
        System.out.println(arrayList); // [Apple, Banana, Orange]
    }
}
```

- **LinkedList**: Implements the List interface using a doubly-linked list. It provides fast insertion and deletion
  operations but slower random access compared to ArrayList.

```java
class main {
    public static void main(String[] args) {
        List<String> linkedList = new LinkedList<>();
        linkedList.add("Apple");
        linkedList.add("Banana");
        linkedList.add("Orange");
        System.out.println(linkedList); // [Apple, Banana, Orange]
    }
} 
```

### Set Interface

The Set interface represents a collection that contains no duplicate elements.

- **HashSet**: Implements the Set interface using a hash table. It does not maintain any order of elements.

```java
public class main {
    public static void main(String[] args) {
        Set<String> hashSet = new HashSet<>();
        hashSet.add("Apple");
        hashSet.add("Banana");
        hashSet.add("Orange");
        System.out.println(hashSet); // [Orange, Banana, Apple]
    }
}
```

- **TreeSet**: Implements the Set interface using a Red-Black tree. It maintains elements in sorted order.

```java
public class main {
    public static void main(String[] args) {
        Set<String> treeSet = new TreeSet<>();
        treeSet.add("Apple");
        treeSet.add("Banana");
        treeSet.add("Orange");
        System.out.println(treeSet); // [Apple, Banana, Orange]
    }
}
```

### Map Interface

The Map interface represents a collection of key-value pairs.

- **HashMap**: Implements the Map interface using a hash table to store key-value pairs. It does not maintain any order
  of elements.

```java
public class main {
    public static void main(String[] args) {
        Map<Integer, String> hashMap = new HashMap<>();
        hashMap.put(1, "Apple");
        hashMap.put(2, "Banana");
        hashMap.put(3, "Orange");
        System.out.println(hashMap); // {1=Apple, 2=Banana, 3=Orange}
    }
}
```

- **TreeMap**: Implements the Map interface using a Red-Black tree to store key-value pairs. It maintains keys in
  sorted order.

```java
public class main {
    public static void main(String[] args) {
        Map<Integer, String> treeMap = new TreeMap<>();
        treeMap.put(1, "Apple");
        treeMap.put(2, "Banana");
        treeMap.put(3, "Orange");
        System.out.println(treeMap); // {1=Apple, 2=Banana, 3=Orange}
    }
}
```

### Concurrent Implementations

Java provides synchronized versions of collection classes to support concurrent access by multiple threads.

- **Vector**: Synchronized version of ArrayList. It is thread-safe but may have performance overhead due to
  synchronization.
- **Hashtable**: Synchronized version of HashMap. It is thread-safe but may have performance overhead due to
  synchronization.
- **Collections.synchronizedList()**: Wraps an ArrayList or LinkedList to make it thread-safe.
- **Collections.synchronizedMap()**: Wraps a HashMap or TreeMap to make it thread-safe.

```java
public class main {
    public static void main(String[] args) {
        List<String> synchronizedList = Collections.synchronizedList(new ArrayList<>());
        Map<Integer, String> synchronizedMap = Collections.synchronizedMap(new HashMap<>());
    }
}
```

Different implementations of the interfaces in the Java Collections API offer various trade-offs in terms of
performance, memory usage, ordering, and thread safety. The choice of implementation depends on the specific
requirements and constraints of the application. Understanding these differences is essential for selecting the
appropriate collection type for a given scenario. Additionally, for concurrent applications, synchronized versions or
concurrent collections from the java.util.concurrent package should be used to ensure thread safety.

### Internal Working of HashSet and HashMap

To understand the internal working of HashSet and HashMap in Java, it's essential to grasp the concepts of hashing and
collision resolution.

#### HashSet

- **Internal Structure**: HashSet is backed by a HashMap. It uses the keys of the HashMap as elements of the HashSet.
  The elements are stored as keys in the HashMap, and the associated values are dummy objects (usually PRESENT).
- **Hashing**: When an element is added to a HashSet, its hash code is computed using the hashCode() method. The
  hash code is used to determine the bucket (index) where the element will be stored in the underlying HashMap.
- **Adding Elements**: To add an element to a HashSet, the element is first hashed to determine its bucket. If the
  bucket is empty, the element is added directly. If the bucket is not empty, collision may occur.
- **Collision Resolution**: If a collision occurs (i.e., two elements have the same hash code), chaining is used for
  collision resolution. In chaining, each bucket in the HashMap maintains a linked list of elements that hash to the
  same bucket. The new element is added to the end of the linked list.

#### HashMap

- **Internal Structure**: HashMap is an implementation of the Map interface and stores key-value pairs. Internally, it
  uses an array of buckets (also known as a table) to store the elements. Each bucket can hold multiple key-value pairs.
- **Hashing**: When a key-value pair is added to a HashMap, the key's hash code is computed using the hashCode() method.
  The hash code is used to determine the bucket where the key-value pair will be stored.
- **Adding Elements**: To add a key-value pair to a HashMap, the key is first hashed to determine its bucket. If the
  bucket is empty, the key-value pair is added directly. If the bucket is not empty, collision may occur.
- **Collision Resolution**: If a collision occurs (i.e., two keys hash to the same bucket), chaining is used for
  collision resolution. Each bucket maintains a linked list of key-value pairs that hash to the same bucket. The new
  key-value pair is added to the end of the linked list.

#### Performance Considerations

- **Load Factor**: Both HashSet and HashMap use a load factor to determine when to resize the underlying array of
  buckets. When the number of elements exceeds the load factor multiplied by the capacity, the array is resized, and the
  elements are rehashed.
- **Capacity**: The initial capacity and load factor can be specified when creating a HashSet or HashMap. Choosing
  appropriate values for these parameters can affect performance and memory usage.

### Creating a Custom Collection in Java

To create a custom collection in Java, you need to implement the Collection interface or extend one of its
sub-interfaces such as List, Set, or Map. Additionally, you may need to implement the Iterator interface to provide an
iterator for your collection. Let's go through the steps to create a custom collection:

**Decide the Type of Collection**

Decide whether you want to create a List, Set, or Map, or if you want to implement a custom collection that doesn't fit
into these categories.

**Implement the Collection Interface**

If you're creating a custom List, Set, or Map, you'll need to implement the respective interface (List, Set, or Map) and
provide implementations for all its methods. If you're creating a custom collection that does not fit into these
categories, you can directly implement the Collection interface.

```java
public class CustomCollection<T> implements Collection<T> {
    // Implement all methods of the Collection interface
}
```

**Implement the Iterator Interface (if needed)**

If your collection needs to be iterable, you'll need to implement the Iterator interface to provide an iterator for your
collection.

```java
public class CustomCollection<T> implements Collection<T> {
    // Implement all methods of the Collection interface

    @Override
    public Iterator<T> iterator() {
        return new CustomIterator<T>(); // Implement CustomIterator class
    }
}
```

**Implement CustomIterator Class (if needed)**

If you've implemented the iterator() method, you'll need to provide an implementation for the CustomIterator class.

```java
public class CustomIterator<T> implements Iterator<T> {
    // Implement all methods of the Iterator interface
}
```

**Test Your Custom Collection**

Once you've implemented your custom collection, make sure to thoroughly test it to ensure that it behaves as expected
and complies with the contracts of the interfaces it implements.

```java
import java.util.Collection;
import java.util.Iterator;

public class CustomCollection<T> implements Collection<T> {

    // Implement all methods of the Collection interface

    @Override
    public int size() {
        // Implementation
    }

    @Override
    public boolean isEmpty() {
        // Implementation
    }

    // Implement other methods such as add(), remove(), contains(), etc.

    @Override
    public Iterator<T> iterator() {
        return new CustomIterator<T>(); // Implement CustomIterator class
    }

    private class CustomIterator<T> implements Iterator<T> {
        // Implement all methods of the Iterator interface
    }
}
```

#### More Detailed Example

Let's create a more detailed example of a custom collection that implements the Collection interface and provides
implementations for methods like add, remove, contains, and others.

```java
import java.util.Collection;
import java.util.Iterator;

public class CustomCollection<T> implements Collection<T> {
    private Object[] elements;
    private int size;
    private static final int DEFAULT_CAPACITY = 10;

    public CustomCollection() {
        this.elements = new Object[DEFAULT_CAPACITY];
        this.size = 0;
    }

    // Implementing Collection interface methods

    @Override
    public int size() {
        return size;
    }

    @Override
    public boolean isEmpty() {
        return size == 0;
    }

    @Override
    public boolean contains(Object o) {
        for (int i = 0; i < size; i++) {
            if (elements[i].equals(o)) {
                return true;
            }
        }
        return false;
    }

    @Override
    public boolean add(T element) {
        if (size == elements.length) {
            // If array is full, resize it
            resize();
        }
        elements[size++] = element;
        return true;
    }

    @Override
    public boolean remove(Object o) {
        for (int i = 0; i < size; i++) {
            if (elements[i].equals(o)) {
                // Found the element to remove
                // Shift elements to the left to remove the element
                System.arraycopy(elements, i + 1, elements, i, size - i - 1);
                elements[--size] = null; // Set last element to null
                return true;
            }
        }
        return false;
    }

    @Override
    public Iterator<T> iterator() {
        return new CustomIterator<>();
    }

    // Other Collection interface methods (addAll, removeAll, clear, etc.) could be implemented
    // similarly

    // Helper method to resize the array when it's full
    private void resize() {
        int newCapacity = elements.length * 2;
        Object[] newArray = new Object[newCapacity];
        System.arraycopy(elements, 0, newArray, 0, size);
        elements = newArray;
    }

    // CustomIterator class
    private class CustomIterator<T> implements Iterator<T> {
        private int cursor;

        @Override
        public boolean hasNext() {
            return cursor < size;
        }

        @Override
        @SuppressWarnings("unchecked")
        public T next() {
            if (hasNext()) {
                return (T) elements[cursor++];
            } else {
                throw new IllegalStateException("No more elements to iterate");
            }
        }
    }
}
```

This CustomCollection class implements the Collection interface and provides implementations for methods like add,
remove, contains, and iterator. It also includes a CustomIterator inner class to provide an iterator for the collection.

You can now use this CustomCollection class to create custom collections with your desired behavior and functionality.
