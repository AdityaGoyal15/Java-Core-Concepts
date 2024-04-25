## Locks in Java

The Lock interface in Java provides a more flexible and powerful alternative to the built-in synchronization mechanism (
synchronized blocks) for controlling access to shared resources in concurrent programming. It allows for finer-grained
control over locking and unlocking and supports features like fairness, interruptibility, and non-blocking attempts to
acquire locks.

Here's an overview of the Lock interface and some of its implementations:

- **Lock Interface**:
  The Lock interface defines the basic behavior of a lock. It includes methods for acquiring and releasing locks,
  checking the lock's state, and supporting more advanced features like interruptible lock acquisition and condition
  variables.

```java
public interface Lock {
    void lock();

    void lockInterruptibly() throws InterruptedException;

    boolean tryLock();

    boolean tryLock(long time, TimeUnit unit) throws InterruptedException;

    void unlock();

    Condition newCondition();
}
```

- **ReentrantLock**:

ReentrantLock is the most commonly used implementation of the Lock interface. It provides reentrant locking, which
means that a thread can acquire the same lock multiple times without deadlocking itself. This allows for nested
synchronization and is similar to the behavior of synchronized blocks.

```java
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class Example {
    private Lock lock = new ReentrantLock();

    public void doSomething() {
        lock.lock();
        try {
            // Critical section
        } finally {
            lock.unlock();
        }
    }
}
```

- **ReentrantReadWriteLock**:

ReentrantReadWriteLock is an implementation of the ReadWriteLock interface, which provides separate locks for reading
and writing operations. Multiple threads can acquire the read lock simultaneously if there are no write locks held,
allowing for concurrent read access. However, only one thread can hold the write lock, ensuring exclusive access during
write operations.

```java
import java.util.concurrent.locks.ReadWriteLock;
import java.util.concurrent.locks.ReentrantReadWriteLock;

public class Example {
    private ReadWriteLock lock = new ReentrantReadWriteLock();

    public void readData() {
        lock.readLock().lock();
        try {
            // Read data
        } finally {
            lock.readLock().unlock();
        }
    }

    public void writeData() {
        lock.writeLock().lock();
        try {
            // Write data
        } finally {
            lock.writeLock().unlock();
        }
    }
}
```

- **StampedLock**:

StampedLock is a relatively new addition to Java's concurrency utilities, introduced in Java 8. It provides three modes
of locking: reading, writing, and optimistic reading. Optimistic reading allows for improved concurrency by avoiding the
use of exclusive locks for read operations when writes are infrequent.

```java
import java.util.concurrent.locks.StampedLock;

public class Example {
    private StampedLock lock = new StampedLock();
    private int data;

    public void modifyData() {
        long stamp = lock.writeLock();
        try {
            // Modify data
        } finally {
            lock.unlockWrite(stamp);
        }
    }

    public int readData() {
        long stamp = lock.readLock();
        try {
            // Read data
            return data;
        } finally {
            lock.unlockRead(stamp);
        }
    }
}
```

These are some of the implementations of the Lock interface in Java. Each implementation offers different features and
trade-offs, allowing developers to choose the most suitable locking mechanism based on their specific concurrency
requirements.

