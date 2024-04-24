## Encapsulation

Encapsulation is another important concept in object-oriented programming (OOP) that involves bundling data (attributes
or properties) and methods (behavior or functionality) within a single unit (object). It allows the internal state of an
object to be protected from outside interference and manipulation, and only exposes a well-defined interface for
interacting with the object's state.

Here's a detailed explanation of encapsulation with an example:

### Example: Encapsulation in a Bank Account System

Suppose we are developing a software system to manage bank accounts. We want to ensure that the internal state of a bank
account, such as balance and account holder information, is properly encapsulated and protected from direct access and
modification.

**Step 1: Define a BankAccount Class**

The first step in encapsulation is to define a class representing a bank account. This class should encapsulate the
account's data and methods for interacting with the account.

```java
public class BankAccount {
    private String accountNumber;
    private double balance;
    private String accountHolderName;

    // Constructor
    public BankAccount(String accountNumber, double initialBalance, String accountHolderName) {
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
        this.accountHolderName = accountHolderName;
    }

    // Methods for interacting with the account
    public void deposit(double amount) {
        balance += amount;
    }

    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        } else {
            System.out.println("Insufficient funds");
        }
    }

    public double getBalance() {
        return balance;
    }

    // Other methods for accessing account information (omitted for brevity)
}
```

In this example, we define a BankAccount class with private instance variables (accountNumber, balance,
accountHolderName) to encapsulate the account's state. We also provide methods (deposit(), withdraw(), getBalance()) for
interacting with the account while maintaining encapsulation.

**Step 2: Use Encapsulation to Interact with Bank Accounts**

Next, we can create objects of the BankAccount class and use encapsulation to interact with them. We can deposit,
withdraw, and inquire about the balance of bank accounts using the provided methods, without directly accessing or
modifying their internal state.

```java
public class Main {
    public static void main(String[] args) {
        // Create a bank account
        BankAccount account = new BankAccount("123456789", 1000.0, "John Doe");

        // Deposit money into the account
        account.deposit(500.0);

        // Withdraw money from the account
        account.withdraw(200.0);

        // Inquire about the account balance
        System.out.println("Account balance: " + account.getBalance());
    }
}
```

In this example, we create a BankAccount object and use its methods (deposit(), withdraw(), getBalance()) to interact
with the account's state. The internal state of the account (accountNumber, balance, accountHolderName) remains
encapsulated within the BankAccount object and cannot be directly accessed or modified from outside the class.

### Benefits of Encapsulation

- Data Hiding: Encapsulation hides the internal state of an object and only exposes a well-defined interface for
  interacting with it, preventing direct access and manipulation of the object's data.
- Modularity: Encapsulation promotes modularity by bundling related data and methods within a single unit (object),
  making it easier to understand, maintain, and extend the code.
- Security: Encapsulation enhances security by restricting access to sensitive data and ensuring that data integrity
  is maintained through controlled access points.

Overall, encapsulation is a fundamental concept in object-oriented programming that promotes data hiding, modularity,
and security. It enables developers to create robust and maintainable software systems by encapsulating the internal
state of objects and providing controlled access to their data and behavior through well-defined interfaces.