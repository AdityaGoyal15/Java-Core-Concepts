## Atomic Operations in Java

The java.util.concurrent.atomic package in Java provides a set of classes that offer atomic operations on single
variables. These classes are designed to support highly concurrent programming by providing thread-safe access to
variables without the need for explicit synchronization. Here are the main classes in this package:

- **AtomicBoolean**:
  This class provides atomic operations on a boolean variable. It includes methods like get(), set(boolean newValue),
  compareAndSet(boolean expect, boolean update), etc.

- **AtomicInteger, AtomicLong, AtomicReference**:
  These classes provide atomic operations on integer, long, and object reference variables respectively. They include
  methods like get(), set(newValue), compareAndSet(expect, update), incrementAndGet(), getAndIncrement(),
  decrementAndGet(), etc.

- **AtomicIntegerArray, AtomicLongArray, AtomicReferenceArray**:
  These classes provide atomic operations on arrays of integers, longs, and object references respectively. They include
  methods like get(index), set(index, newValue), compareAndSet(index, expect, update), incrementAndGet(index),
  getAndIncrement(index), decrementAndGet(index), etc.

- **AtomicIntegerFieldUpdater, AtomicLongFieldUpdater, AtomicReferenceFieldUpdater**:
  These are generic classes that provide atomic updates to volatile fields of objects. They allow you to perform atomic
  operations on fields without directly using AtomicInteger, AtomicLong, or AtomicReference.

- **AtomicMarkableReference, AtomicStampedReference**:
  These classes provide atomic operations on object references with an associated mark or stamp. They are useful for
  implementing lock-free data structures and algorithms.

- **Striped64**:
  This class is a common superclass for classes providing atomic updates to variables representing aggregate statistics
  or accumulators.

### How AtomicInteger is different from a primitive int accessed from a synchronized block

An AtomicInteger is a class in Java's java.util.concurrent.atomic package that provides atomic operations on integers.
Atomic operations are those that are performed as a single, indivisible unit, meaning they are not subject to
interference from other threads. This ensures thread safety without the need for explicit synchronization.

Here's how an AtomicInteger works:

- It encapsulates an integer value and provides methods for performing atomic operations on that value, such as get(),
  set(), incrementAndGet(), getAndIncrement(), compareAndSet(), etc.
- These operations are guaranteed to be atomic, meaning they are executed without interference from other threads.
  They ensure that no other thread can observe the value of the integer in an inconsistent state during the operation.

When accessed within a synchronized block, the behavior of an AtomicInteger and a primitive integer differs in terms of
performance and locking granularity:

- **Primitive Integer with Synchronized Block**:
  If you use a primitive integer (e.g., int) within a synchronized block, you need to synchronize access to it
  explicitly to ensure thread safety. This means that only one thread can execute the synchronized block at a time,
  preventing concurrent access and potential data corruption.

```java
public class Main {
    private int counter = 0;

    public synchronized void increment() {
        counter++;
    }
}
```

- **AtomicInteger**

If you use an AtomicInteger, you don't need to use synchronized blocks explicitly because the atomic operations
provided by AtomicInteger inherently ensure thread safety. These operations are performed atomically, without the need
for explicit synchronization.

```java
public class Main {
    private AtomicInteger counter = new AtomicInteger(0);

    public void increment() {
        counter.incrementAndGet();
    }
}
```

The difference lies in the implementation details:

- Using AtomicInteger avoids the overhead of synchronization that comes with using synchronized blocks, as atomic
  operations are implemented more efficiently at the hardware level or using lock-free algorithms.
- With AtomicInteger, you achieve thread safety without the risk of deadlocks or contention that can occur with
  synchronized blocks, especially in scenarios with high contention.

In summary, AtomicInteger provides a more efficient and safer alternative to using synchronized blocks with primitive
integers when you need to ensure thread safety in concurrent environments.