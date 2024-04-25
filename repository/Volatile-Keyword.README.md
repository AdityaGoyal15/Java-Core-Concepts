## Volatile keyword in Java

In Java, the volatile keyword is used to indicate that a variable's value may be changed by multiple threads
simultaneously. When a variable is declared as volatile, the Java memory model ensures that any thread reading the
variable sees the most recent write to that variable by any other thread. This ensures visibility of changes across
threads without the need for explicit synchronization.

Here are the key aspects of the volatile keyword:

- **Visibility**: Changes made to a volatile variable by one thread are immediately visible to other threads. This
  ensures that all threads see a consistent view of shared data.

- **No Atomicity or Orderliness**: While volatile ensures visibility, it does not provide atomicity for compound
  actions (like incrementing a counter) nor does it guarantee the order of operations. For operations that require both
  visibility and atomicity, you'll need to use other synchronization mechanisms like locks or atomic classes.

- **Preventing Compiler Optimizations**: The volatile keyword also prevents certain compiler optimizations that might
  reorder or cache accesses to the variable. This ensures that reads and writes to volatile variables are not optimized
  away or reordered in a way that could affect program correctness in a multithreaded environment.

Here's an example illustrating the use of the volatile keyword:

```java
public class SharedData {
    private volatile int counter = 0;

    public void increment() {
        counter++; // Compound action: read, increment, write
    }

    public int getCounter() {
        return counter;
    }
}
```

In this example, the counter variable is declared as volatile. Any changes made to counter by one thread will be
immediately visible to other threads. However, it's important to note that the increment() method is not atomic, so
multiple threads incrementing the counter concurrently may lead to incorrect results without additional synchronization.

In summary, the volatile keyword is used in Java to ensure visibility of shared variables across threads. It's
particularly useful when variables are accessed by multiple threads without requiring synchronization for access, though
it does not provide atomicity or enforce order of operations.