# Java Exceptions

## Runtime Exceptions

### 1. NullPointerException

Occurs when we try to use an object that contains null.

### 2. ArrayIndexOutOfBoundsException

Occurs when we access an invalid array index.

Example:

int[] numbers = {10, 20, 30};

System.out.println(numbers[5]);
# Java Exceptions – Complete Notes

## 1. What is an Exception?

An **exception** is an unwanted event that occurs during program execution and interrupts the normal flow of the program.

Example:

```java
int a = 10;
int b = 0;

System.out.println(a / b);
```

This results in:

```text
ArithmeticException: / by zero
```

---

# 2. Java Exception Hierarchy

```text
                    Object
                       |
                   Throwable
                  /         \
               Error       Exception
               /              |
          StackOverflow    RuntimeException
          OutOfMemoryError      |
                            ----------------
                            |              |
                       Checked         Unchecked
                       Exceptions      Exceptions
```

More accurately:

```text
Throwable
├── Error
│   ├── OutOfMemoryError
│   ├── StackOverflowError
│   └── AssertionError
│
└── Exception
    ├── RuntimeException
    │   ├── NullPointerException
    │   ├── ArithmeticException
    │   ├── ArrayIndexOutOfBoundsException
    │   ├── StringIndexOutOfBoundsException
    │   ├── NumberFormatException
    │   ├── ClassCastException
    │   └── IllegalArgumentException
    │
    └── Checked Exceptions
        ├── IOException
        ├── SQLException
        ├── FileNotFoundException
        ├── InterruptedException
        └── ClassNotFoundException
```

---

# 3. Checked Exceptions

Checked exceptions are checked by the **compiler**.

The programmer must either:

1. Handle the exception using `try-catch`
2. Declare it using `throws`

Examples:

```java
IOException
SQLException
InterruptedException
FileNotFoundException
ClassNotFoundException
```

Example:

```java
import java.io.FileReader;
import java.io.IOException;

public class Test {

    public static void main(String[] args) {

        try {
            FileReader file = new FileReader("test.txt");
        }
        catch (IOException e) {
            System.out.println("File not found");
        }
    }
}
```

---

# 4. Unchecked Exceptions

Unchecked exceptions occur during runtime.

They are subclasses of:

```java
RuntimeException
```

Examples:

```java
NullPointerException
ArithmeticException
ArrayIndexOutOfBoundsException
StringIndexOutOfBoundsException
NumberFormatException
ClassCastException
IllegalArgumentException
```

The compiler does not force you to handle them.

Example:

```java
int a = 10;
int b = 0;

System.out.println(a / b);
```

Result:

```text
ArithmeticException
```

---

# 5. Common Java Exceptions

## 5.1 NullPointerException

Occurs when trying to use an object that contains `null`.

```java
String name = null;

System.out.println(name.length());
```

Result:

```text
NullPointerException
```

Correct approach:

```java
String name = null;

if (name != null) {
    System.out.println(name.length());
}
```

---

# 5.2 ArithmeticException

Occurs when an invalid arithmetic operation is performed.

Most commonly division by zero.

```java
int a = 10;
int b = 0;

System.out.println(a / b);
```

Result:

```text
ArithmeticException
```

---

# 5.3 ArrayIndexOutOfBoundsException

Occurs when accessing an array using an invalid index.

```java
int[] numbers = {10, 20, 30};

System.out.println(numbers[5]);
```

Valid indexes are:

```text
0
1
2
```

Index `5` does not exist.

---

# 5.4 StringIndexOutOfBoundsException

Occurs when accessing an invalid character position in a String.

```java
String name = "Java";

System.out.println(name.charAt(10));
```

Result:

```text
StringIndexOutOfBoundsException
```

Valid indexes:

```text
0 1 2 3
```

---

# 5.5 NumberFormatException

Occurs when converting an invalid String into a number.

```java
String value = "ABC";

int number = Integer.parseInt(value);
```

Result:

```text
NumberFormatException
```

Valid example:

```java
String value = "100";

int number = Integer.parseInt(value);

System.out.println(number);
```

---

# 5.6 ClassCastException

Occurs when trying to cast an object to an incompatible type.

```java
Object obj = "Java";

Integer number = (Integer) obj;
```

Result:

```text
ClassCastException
```

---

# 5.7 IllegalArgumentException

Occurs when a method receives an inappropriate argument.

Example:

```java
Thread thread = new Thread();

thread.setPriority(20);
```

Valid thread priority is:

```text
1 - 10
```

Therefore:

```text
IllegalArgumentException
```

---

# 5.8 IllegalStateException

Occurs when a method is called at an inappropriate time or state.

Example:

```java
Thread thread = new Thread();

thread.start();
thread.start();
```

Calling `start()` again on the same thread can result in:

```text
IllegalThreadStateException
```

---

# 5.9 ConcurrentModificationException

Occurs when a collection is structurally modified while iterating over it in an unsupported way.

Example:

```java
List<String> names = new ArrayList<>();

names.add("Java");
names.add("Selenium");

for (String name : names) {

    if (name.equals("Java")) {
        names.remove(name);
    }
}
```

This can result in:

```text
ConcurrentModificationException
```

---

# 6. Checked Exception Examples

## IOException

Used for input/output operations.

```java
try {
    FileReader file = new FileReader("test.txt");
}
catch (IOException e) {
    e.printStackTrace();
}
```

---

## FileNotFoundException

Occurs when a requested file cannot be found.

```java
FileReader file = new FileReader("abc.txt");
```

If the file doesn't exist:

```text
FileNotFoundException
```

`FileNotFoundException` is a subclass of `IOException`.

---

## SQLException

Used when database operations encounter an error.

```java
try {
    Connection con =
        DriverManager.getConnection(url, username, password);
}
catch (SQLException e) {
    e.printStackTrace();
}
```

---

## InterruptedException

Occurs when a thread is interrupted while it is waiting, sleeping, or otherwise blocked.

```java
try {
    Thread.sleep(5000);
}
catch (InterruptedException e) {
    e.printStackTrace();
}
```

---

## ClassNotFoundException

Occurs when Java cannot find a requested class.

```java
Class.forName("com.mysql.jdbc.Driver");
```

If the class is unavailable:

```text
ClassNotFoundException
```

---

# 7. try-catch

Used to handle exceptions.

```java
try {

    int result = 10 / 0;

}
catch (ArithmeticException e) {

    System.out.println("Cannot divide by zero");

}
```

---

# 8. Multiple catch Blocks

```java
try {

    int[] numbers = {10, 20, 30};

    System.out.println(numbers[5]);

}
catch (ArithmeticException e) {

    System.out.println("Arithmetic error");

}
catch (ArrayIndexOutOfBoundsException e) {

    System.out.println("Invalid array index");

}
catch (Exception e) {

    System.out.println("Some other exception");

}
```

### Important

Always put the **specific exception before the generic exception**.

Correct:

```java
catch (ArithmeticException e) {
}
catch (Exception e) {
}
```

Incorrect:

```java
catch (Exception e) {
}
catch (ArithmeticException e) {
}
```

The second version causes a compilation error because `ArithmeticException` has already been caught by `Exception`.

---

# 9. finally

`finally` is used for code that should normally execute whether an exception occurs or not.

```java
try {

    System.out.println("Try");

}
catch (Exception e) {

    System.out.println("Catch");

}
finally {

    System.out.println("Finally");

}
```

Output:

```text
Try
Finally
```

---

# 10. Can finally be used without catch?

Yes.

```java
try {

    System.out.println("Try");

}
finally {

    System.out.println("Finally");

}
```

A `try` block must be followed by at least one of:

```text
catch
finally
```

Therefore:

```java
try {
}
finally {
}
```

is valid.

But:

```java
try {
}
```

is invalid.

---

# 11. throw

`throw` is used to explicitly throw an exception.

```java
int age = 15;

if (age < 18) {

    throw new IllegalArgumentException("Age must be 18 or above");

}
```

---

# 12. throws

`throws` is used in a method declaration to indicate that the method may throw an exception.

```java
public void readFile() throws IOException {

    FileReader file = new FileReader("test.txt");

}
```

The caller must handle the exception or declare it further.

---

# 13. throw vs throws

| throw                                 | throws                          |
| ------------------------------------- | ------------------------------- |
| Used to explicitly throw an exception | Used to declare exceptions      |
| Used inside method                    | Used in method signature        |
| Throws one exception at a time        | Can declare multiple exceptions |
| Followed by exception object          | Followed by exception class     |

Example:

```java
throw new ArithmeticException();
```

```java
public void test() throws IOException, SQLException {
}
```

---

# 14. Error vs Exception

## Error

Errors generally represent serious problems that applications normally should not try to recover from.

Examples:

```text
OutOfMemoryError
StackOverflowError
```

## Exception

Exceptions are conditions that an application can often handle.

Examples:

```text
IOException
SQLException
NullPointerException
ArithmeticException
```

---

# 15. Selenium Common Exceptions

When working with Selenium, these exceptions are especially important for interviews.

## NoSuchElementException

Element cannot be found.

```java
driver.findElement(By.id("username"));
```

Possible reasons:

* Wrong locator
* Element not present
* Page not loaded
* Incorrect frame
* Dynamic element

---

## NoSuchWindowException

Occurs when Selenium tries to switch to a window that does not exist.

```java
driver.switchTo().window("invalidWindow");
```

---

## NoSuchFrameException

Occurs when Selenium cannot find the specified frame.

```java
driver.switchTo().frame("invalidFrame");
```

---

## NoAlertPresentException

Occurs when Selenium tries to interact with an alert that isn't present.

```java
driver.switchTo().alert();
```

---

## ElementNotInteractableException

Element exists but cannot currently be interacted with.

Example:

```java
driver.findElement(By.id("submit")).click();
```

Possible reasons:

* Element hidden
* Element disabled
* Element not ready

---

## ElementClickInterceptedException

Another element is blocking the element you are trying to click.

```java
driver.findElement(By.id("submit")).click();
```

Possible causes:

* Popup
* Overlay
* Another element covering the button

---

## StaleElementReferenceException

Occurs when the element reference is no longer attached to the DOM.

Common with dynamic web pages.

Example:

```java
WebElement element = driver.findElement(By.id("name"));

driver.navigate().refresh();

element.click();
```

The old element reference may become stale.

---

## TimeoutException

Occurs when an expected condition is not satisfied within the specified timeout.

```java
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));

wait.until(ExpectedConditions.visibilityOfElementLocated(
    By.id("username")
));
```

---

## InvalidSelectorException

Occurs when an invalid XPath or CSS selector is used.

```java
driver.findElement(By.xpath("//*["));
```

---

## InvalidArgumentException

Occurs when an invalid argument is passed to a Selenium method.

---

## SessionNotCreatedException

Occurs when a WebDriver session cannot be created.

Common causes:

* Browser/driver incompatibility
* Invalid browser configuration
* Incorrect capabilities

---

## WebDriverException

A general Selenium WebDriver exception.

Many Selenium-specific exceptions inherit from:

```java
WebDriverException
```

---

# 16. Selenium Exception Handling Example

```java
try {

    WebElement element =
        driver.findElement(By.id("username"));

    element.click();

}
catch (NoSuchElementException e) {

    System.out.println("Element not found");

}
catch (ElementNotInteractableException e) {

    System.out.println("Element cannot be interacted with");

}
catch (TimeoutException e) {

    System.out.println("Element timed out");

}
catch (WebDriverException e) {

    System.out.println("Selenium WebDriver error");

}
finally {

    driver.quit();

}
```

---

# 17. Most Important Exceptions for Selenium Interviews

Remember these:

```text
NoSuchElementException
StaleElementReferenceException
ElementNotInteractableException
ElementClickInterceptedException
TimeoutException
NoSuchWindowException
NoSuchFrameException
NoAlertPresentException
InvalidSelectorException
SessionNotCreatedException
WebDriverException
```

---

# 18. Quick Interview Comparison

### Checked vs Unchecked

```text
Checked Exception
      ↓
Compiler checks it
      ↓
Must handle or declare
      ↓
IOException
SQLException
InterruptedException
```

```text
Unchecked Exception
      ↓
RuntimeException
      ↓
Compiler does not force handling
      ↓
NullPointerException
ArithmeticException
NumberFormatException
ArrayIndexOutOfBoundsException
```

---

# 19. Easy Way to Remember

### Checked

Think:

**"Compiler asks me to handle it."**

Examples:

```text
IOException
SQLException
InterruptedException
FileNotFoundException
ClassNotFoundException
```

### Unchecked

Think:

**"Problem happens while program is running."**

Examples:

```text
NullPointerException
ArithmeticException
NumberFormatException
ArrayIndexOutOfBoundsException
StringIndexOutOfBoundsException
ClassCastException
IllegalArgumentException
```

### Selenium

Think:

**"Element, Window, Frame, Alert, Timeout."**

```text
NoSuchElementException
StaleElementReferenceException
ElementNotInteractableException
ElementClickInterceptedException
NoSuchWindowException
NoSuchFrameException
NoAlertPresentException
TimeoutException
```
