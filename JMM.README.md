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