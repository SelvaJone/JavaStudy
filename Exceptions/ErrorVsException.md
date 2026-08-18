## Error in Java

An **Error** is a serious problem that occurs during the execution of a Java application. Errors are generally caused by problems related to the **JVM, memory, system resources, or the runtime environment**, rather than by normal application logic.

Errors are subclasses of the `java.lang.Error` class, which itself extends `Throwable`.

Unlike exceptions, errors are generally **not expected to be handled by application code**. In most cases, the best approach is to identify and fix the underlying problem rather than trying to recover from the error using `try-catch`.

### Common Java Errors

Some commonly encountered errors are:

```text
OutOfMemoryError
StackOverflowError
NoClassDefFoundError
ExceptionInInitializerError
AssertionError
```

### 1. OutOfMemoryError

`OutOfMemoryError` occurs when the JVM cannot allocate enough memory for new objects.

Example:

```java
public class Test {

    public static void main(String[] args) {

        int[] numbers = new int[Integer.MAX_VALUE];

    }
}
```

The JVM may not have enough memory to create such a large array.

Result:

```text
OutOfMemoryError: Java heap space
```

Common causes:

* Creating too many objects
* Large collections consuming memory
* Memory leaks
* Loading very large files into memory
* Insufficient JVM heap size

---

### 2. StackOverflowError

`StackOverflowError` usually occurs when a method calls itself recursively without a proper termination condition.

Example:

```java
public class Test {

    static void display() {

        display();

    }

    public static void main(String[] args) {

        display();

    }
}
```

Here, `display()` continuously calls itself.

Eventually, the JVM's stack memory is exhausted.

Result:

```text
StackOverflowError
```

Correct recursion should have a termination condition:

```java
static void display(int count) {

    if (count == 0) {
        return;
    }

    System.out.println(count);

    display(count - 1);
}
```

---

### 3. NoClassDefFoundError

`NoClassDefFoundError` occurs when the JVM tries to load a class that was available during compilation but cannot be found at runtime.

This can happen because:

* Required JAR is missing
* Classpath is incorrect
* Dependency is not available at runtime
* Deployment is incomplete

Example situation:

```text
Application compiled successfully
        ↓
Application starts
        ↓
JVM tries to load a class
        ↓
Required class is missing
        ↓
NoClassDefFoundError
```

This is different from `ClassNotFoundException`.

### ClassNotFoundException vs NoClassDefFoundError

| ClassNotFoundException                          | NoClassDefFoundError                                              |
| ----------------------------------------------- | ----------------------------------------------------------------- |
| An exception                                    | An error                                                          |
| Usually occurs when dynamically loading a class | Class was available during compilation but unavailable at runtime |
| Checked exception                               | Error                                                             |
| Can be handled using `try-catch`                | Usually indicates a configuration/dependency problem              |

---

### 4. ExceptionInInitializerError

This error can occur when an exception happens while initializing a static field or static block.

Example:

```java
public class Test {

    static int number = 10 / 0;

    public static void main(String[] args) {

        System.out.println(number);

    }
}
```

The static initialization fails before the application can properly use the class.

Result:

```text
ExceptionInInitializerError
```

---

### 5. AssertionError

`AssertionError` occurs when an assertion fails.

Example:

```java
int age = 15;

assert age >= 18 : "Age must be 18 or above";
```

If assertions are enabled and the condition is false:

```text
AssertionError: Age must be 18 or above
```

Assertions are commonly used to verify assumptions during development and testing.

---

# Error vs Exception

The major difference between an **Error** and an **Exception** is the type of problem they represent.

An **Exception** generally represents a condition that an application may be able to handle, such as a missing file, invalid input, database problem, or an element not being found in Selenium.

An **Error**, on the other hand, generally represents a more serious problem involving the JVM or runtime environment, such as insufficient memory or stack exhaustion.

```text
Throwable
│
├── Error
│   ├── OutOfMemoryError
│   ├── StackOverflowError
│   ├── NoClassDefFoundError
│   └── AssertionError
│
└── Exception
    ├── Checked Exception
    │   ├── IOException
    │   ├── SQLException
    │   └── InterruptedException
    │
    └── RuntimeException
        ├── NullPointerException
        ├── ArithmeticException
        ├── NumberFormatException
        └── ArrayIndexOutOfBoundsException
```

## Should We Catch an Error?

Technically, Java allows you to catch an `Error` because both `Error` and `Exception` extend `Throwable`.

Example:

```java
try {

    // code

}
catch (OutOfMemoryError e) {

    System.out.println("Memory problem");

}
```

However, **you generally should not catch serious JVM errors just to continue execution**. Instead, investigate and fix the underlying cause.

For example:

* `OutOfMemoryError` → investigate memory usage
* `StackOverflowError` → fix recursion or excessive call depth
* `NoClassDefFoundError` → check dependencies/classpath
* `ExceptionInInitializerError` → check static initialization

### Interview Point

> **Exception represents a condition that an application may be able to recover from, whereas Error generally represents a serious JVM or runtime problem that an application normally should not attempt to recover from.**

### Simple Memory Trick

```text
Exception → Application problem → Usually handle it

Error → JVM/System-level problem → Usually fix the root cause
```
