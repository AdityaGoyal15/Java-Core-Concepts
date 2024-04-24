## equals() & hashcode() methods

In Java, the equals() and hashCode() methods are closely related and are used for comparing objects and storing objects
in collections such as HashMap, HashSet, etc. Understanding the contract between these methods is crucial for proper
functioning of collections and for maintaining consistency in your code.

### equals() method

The equals() method is used to compare the equality of two objects. It is defined in the Object class and is overridden
in most classes to provide custom equality comparison based on the object's state.

The general contract for the equals() method is as follows:

- **Reflexive**: For any non-null reference value x, x.equals(x) should return true.
- **Symmetric**: For any non-null reference values x and y, if x.equals(y) returns true, then y.equals(x) should also
  return true.
- **Transitive**: For any non-null reference values x, y, and z, if x.equals(y) returns true and y.equals(z) returns
  true, then x.equals(z) should also return true.
- **Consistent**: For any non-null reference values x and y, multiple invocations of x.equals(y) consistently return
  either true or false, provided that the objects referenced by x and y remain unchanged.
- **Null Comparison**: For any non-null reference value x, x.equals(null) should return false.

### hashcode() method

The hashCode() method returns a hash code value for the object, which is used by hash-based data structures like
HashMap, HashSet, etc. to determine the bucket where the object should be stored.

The general contract for the hashCode() method is as follows:

- **Consistency with equals()**: If two objects are equal according to the equals() method, then calling hashCode() on
  each of the objects must produce the same integer result.
- **Consistent Hashing**: The hash code value of an object should remain consistent over multiple invocations of the
  hashCode() method, as long as the object's state relevant to equality comparison does not change.
- **Collision Minimization**: Different objects should ideally produce different hash codes to minimize the chances of
  collisions in hash-based data structures. However, it is possible for different objects to have the same hash code (
  collisions), in which case the data structure should handle them gracefully.

### Contract between equals() and hashCode()

The contract between equals() and hashCode() is such that if two objects are equal according to the equals() method,
then they must have the same hash code value. Conversely, if two objects have the same hash code value, it does not
necessarily mean that they are equal (though good hash functions try to minimize collisions).

To fulfill this contract, whenever you override the equals() method in a class, you should also override the hashCode()
method to ensure consistency between equality comparison and hashing.

```java

@Override
public boolean equals(Object obj) {
    // Custom equality comparison
}

@Override
public int hashCode() {
    // Custom hash code calculation
}
```

By following the contract between equals() and hashCode(), you ensure that objects behave correctly when used in
hash-based collections and that equality comparison and hashing are consistent with each other.