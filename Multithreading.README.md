## Multithreading

Multithreading is a specific technique for achieving concurrency by dividing a program into multiple threads of
execution. Threads are lightweight units of execution that run concurrently within the same process. Multithreading
allows a program to perform multiple tasks simultaneously by executing different parts of the program (or different
tasks) concurrently in separate threads.

Key points about multithreading:

- **Thread-Based Concurrency**: Multithreading achieves concurrency by utilizing multiple threads of execution within a
  single process.
- **Shared Memory**: Threads within the same process share the same memory space, allowing them to communicate and
  synchronize through shared data structures and variables.
- **Resource Sharing**: Multithreading allows multiple threads to share resources such as CPU time, memory, and I/O
  devices.
- **Context Switching**: Multithreading involves context switching, where the processor switches between executing
  different threads, allowing them to progress concurrently.

In summary, concurrency is a broader concept that refers to the management of multiple tasks or processes executing
concurrently, while multithreading is a specific technique for achieving concurrency by using multiple threads within a
single process. Multithreading is one of the primary mechanisms for implementing concurrency in modern programming
languages and operating systems.

### Creating Threads in Java

In Java, multithreading can be achieved by extending the Thread class or implementing the Runnable interface. Here's an
example using both approaches:

**Approach 1: Extending Thread class**

```java
class MyThread extends Thread {
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println("Thread 1: " + i);
            try {
                Thread.sleep(1000); // Pause execution for 1 second
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread thread1 = new MyThread();
        thread1.start(); // Start the thread
    }
}
```

**Approach 2: Implementing Runnable interface**

```java
class MyRunnable implements Runnable {
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println("Thread 2: " + i);
            try {
                Thread.sleep(1000); // Pause execution for 1 second
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Thread thread2 = new Thread(new MyRunnable());
        thread2.start(); // Start the thread
    }
}
```

**Approach 3: Using Lambda Expressions**

Starting from Java 8, you can use lambda expressions to define the thread's logic inline when implementing the Runnable
interface.

```java
public class Main {
    public static void main(String[] args) {
        Runnable myRunnable =
                () -> {
                    // Thread logic goes here
                };
        Thread thread = new Thread(myRunnable);
        thread.start(); // Start the thread
    }
}
```

**Approach 4: Using Anonymous Inner Class**

```java
public class Main {
    public static void main(String[] args) {
        Thread thread =
                new Thread(
                        new Runnable() {
                            public void run() {
                                // Thread logic goes here
                            }
                        });
        thread.start(); // Start the thread
    }
}
```

**Approach 5: Executor Framework**

Java provides the Executor framework in the java.util.concurrent package, which provides a higher-level abstraction for
managing threads. You can submit tasks to an executor for execution, and it handles thread creation, pooling, and
lifecycle management.

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Main {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newSingleThreadExecutor();
        executor.submit(
                () -> {
                    // Thread logic goes here
                });
        executor.shutdown(); // Shutdown the executor after use
    }
}
```

### Synchronization

When multiple threads access shared resources concurrently, synchronization is necessary to avoid race conditions and
ensure data consistency. Here's an example illustrating synchronization using the synchronized keyword:

```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public synchronized int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();

        Runnable task =
                () -> {
                    for (int i = 0; i < 1000; i++) {
                        counter.increment();
                    }
                };

        Thread thread1 = new Thread(task);
        Thread thread2 = new Thread(task);

        thread1.start();
        thread2.start();

        try {
            thread1.join();
            thread2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Final Count: " + counter.getCount());
    }
}
```

### Thread Communication

Threads can communicate and synchronize their actions using methods such as wait(), notify(), and notifyAll(). Here's an
example illustrating thread communication:

```java
class Message {
    private String message;
    private boolean isMessageDelivered = false;

    public synchronized void setMessage(String message) {
        while (isMessageDelivered) {
            try {
                wait(); // Wait until message is delivered
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        this.message = message;
        isMessageDelivered = true;
        notify(); // Notify waiting threads
    }

    public synchronized String getMessage() {
        while (!isMessageDelivered) {
            try {
                wait(); // Wait until message is delivered
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        isMessageDelivered = false;
        notify(); // Notify waiting threads
        return message;
    }
}

public class Main {
    public static void main(String[] args) {
        Message message = new Message();

        Runnable sender =
                () -> {
                    for (int i = 1; i <= 5; i++) {
                        message.setMessage("Message " + i);
                        System.out.println("Sent: " + message.getMessage());
                    }
                };

        Runnable receiver =
                () -> {
                    for (int i = 1; i <= 5; i++) {
                        System.out.println("Received: " + message.getMessage());
                    }
                };

        Thread senderThread = new Thread(sender);
        Thread receiverThread = new Thread(receiver);

        senderThread.start();
        receiverThread.start();
    }
}
```

These examples demonstrate the basic concepts of multithreading in Java, including thread creation, synchronization, and
thread communication. Understanding these concepts is essential for developing concurrent and scalable applications in
Java.

Let's explore some common methods and concepts related to multithreading in Java:

**start()**

The start() method is used to start the execution of a thread. When called, it allocates a new call stack for the
thread, initializes the thread, and invokes the run() method of the thread. It should be noted that you should not call
the run() method directly to start a thread; instead, use the start() method.

```java
Thread thread = new Thread(() -> {
    // Thread logic
});
thread.start(); // Start the thread
```

**run()**

The run() method contains the code that constitutes the execution of the thread. It is called by the JVM when the
start() method is invoked on the thread. You override this method to define the behavior of your thread.

```java
class MyThread extends Thread {
    public void run() {
        // Thread logic
    }
}
```

**join()**

The join() method allows one thread to wait for the completion of another thread. It blocks the calling thread until the
thread on which it is called completes its execution or a specified timeout occurs.

```java
Thread thread = new Thread(() -> {
    // Thread logic
});
thread.start(); // Start the thread
try{
    thread.join(); // Wait for the thread to complete
} catch(InterruptedException e) {
    e.printStackTrace();
}
```

**sleep()**

The sleep() method pauses the execution of the current thread for a specified amount of time, allowing other threads to
execute. It can be used for simple thread synchronization or to introduce delays in thread execution.

```java
try {
    Thread.sleep(1000); // Pause execution for 1 second
} catch(InterruptedException e) {
    e.printStackTrace();
}
```

**yield()**

The yield() method is used to voluntarily give up the CPU by the currently executing thread, allowing other threads of
the same priority to execute. It is a hint to the scheduler that the thread is willing to yield its current use of the
CPU.

```java
Thread.yield(); // Yield the CPU to other threads
```

**interrupt()**

The interrupt() method is used to interrupt the execution of a thread. It sets the interrupt status of the thread,
causing it to throw an InterruptedException if it is in a blocked or waiting state.

```java
Thread thread = new Thread(() -> {
    while (!Thread.currentThread().isInterrupted()) {
        // Thread logic
    }
});
thread.start(); // Start the thread
thread.interrupt(); // Interrupt the thread
```

**isInterrupted()**

The isInterrupted() method checks whether the current thread has been interrupted. It returns true if the thread has
been interrupted; otherwise, it returns false.

```java
if (Thread.currentThread().isInterrupted()) {
    // Thread has been interrupted
}
```

**wait(), notify(), notifyAll()**

These methods are used for inter-thread communication and synchronization. They are typically used in conjunction with
synchronization blocks or methods to coordinate the execution of multiple threads.

- **wait()**: Causes the current thread to wait until another thread invokes the notify() or notifyAll() method for the
  same object.
- **notify()**: Wakes up a single thread that is waiting on the object.
- **notifyAll()**: Wakes up all threads that are waiting on the object.

```java
class Message {
    public synchronized void setMessage(String message) {
        // Set message
        notify(); // Notify waiting threads
    }

    public synchronized String getMessage() {
        // Get message
        wait(); // Wait for message to be set
        return message;
    }
}
```

These are some of the key methods and concepts related to multithreading in Java. Understanding how to use these methods
effectively is essential for developing concurrent and scalable applications.