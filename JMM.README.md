## Memory Model

The Java Memory Model (JMM) defines how the Java virtual machine (JVM) works with the computer's memory architecture to
provide a consistent and predictable behavior for multi-threaded Java programs. It specifies the rules and guarantees
regarding how changes made by one thread to shared variables are made visible to other threads.

Key concepts of the Java Memory Model include:

- Main Memory: This is the primary memory area where all variables are stored. It is shared among all threads running in
  the JVM.
- Thread: A thread is a unit of execution within a process. In Java, multiple threads can run concurrently within a
  single process.
- Thread Local Memory: Each thread has its own thread-local memory, which may contain a cache of variables from main
  memory.
- Shared Variables: Shared variables are variables accessed by multiple threads. Access to shared variables by multiple
  threads can lead to data races and concurrency issues.
- Visibility Guarantees: The Java Memory Model provides visibility guarantees to ensure that changes made by one thread
  to shared variables are visible to other threads. These guarantees are provided through synchronization mechanisms
  such as synchronized blocks, volatile variables, and Lock interfaces.
- Happens-Before Relationship: The happens-before relationship is a partial ordering of memory operations that
  determines when changes made by one thread become visible to other threads. It is established by synchronization
  actions such as acquiring and releasing locks, and by other special relationships defined in the JMM.
- Atomicity: Certain operations in Java are atomic, meaning that they are performed as a single, indivisible unit. For
  example, operations on volatile variables, synchronized blocks, and atomic classes from the java.util.concurrent
  package are atomic.
- Memory Consistency: The JMM defines the memory consistency properties that must be preserved when accessing shared
  variables in multithreaded programs. These properties ensure that the behavior of multithreaded programs is
  predictable and consistent across different JVM implementations and hardware architectures.

Overall, the Java Memory Model provides a set of rules and guidelines for writing correct and efficient multithreaded
Java programs. Understanding these concepts is crucial for writing thread-safe code and avoiding concurrency issues
such as data races, deadlocks, and inconsistent state.

In JDK 8, one of the significant changes related to memory management was the removal of the Permanent Generation (
PermGen) space. The PermGen space was a special area of the Java heap used to store metadata about classes, methods, and
other runtime artifacts, including interned strings and class metadata.

Before JDK 8, PermGen space had several limitations and issues:

- Fixed Size: PermGen space had a fixed size that was specified using the -XX:MaxPermSize JVM option. This size was
  typically set at JVM startup and couldn't be dynamically adjusted at runtime.
- Out of Memory Errors: PermGen space could become a source of OutOfMemoryError exceptions, especially in applications
  that dynamically loaded and unloaded classes at runtime (e.g., web applications using frameworks like Spring or
  Hibernate). This was often observed in long-running applications, such as application servers, where classloader leaks
  could lead to PermGen exhaustion.

To address these limitations and improve the memory management model, JDK 8 introduced the following changes:

- Class Metadata Storage: Class metadata, including information about classes, methods, and other runtime artifacts, was
  moved from PermGen space to the native heap. This metadata is now stored in the "Metaspace," which is a native memory
  area managed by the JVM.
- Dynamic Sizing: Unlike PermGen space, which had a fixed size, Metaspace can dynamically resize itself based on
  application demand. Metaspace automatically grows and shrinks as needed, helping to prevent OutOfMemoryError
  situations related to class metadata.
- Garbage Collection: Metaspace memory is managed by the garbage collector, and unused class metadata can be reclaimed
  during garbage collection cycles. This allows the JVM to reclaim memory occupied by unused classes and reduce memory
  fragmentation over time.
- JVM Options: With the removal of PermGen space, JVM options related to PermGen, such as -XX:MaxPermSize, are no longer
  valid in JDK 8 and later versions. Instead, you can use -XX:MaxMetaspaceSize to specify the maximum size of the
  Metaspace.

Overall, the removal of PermGen space and the introduction of Metaspace in JDK 8 improved the memory management model
in Java, making it more flexible, efficient, and resilient to memory-related issues in modern Java applications.
Developers no longer need to manually tune PermGen space parameters and are less likely to encounter PermGen-related
errors in their applications.