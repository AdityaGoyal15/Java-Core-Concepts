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

