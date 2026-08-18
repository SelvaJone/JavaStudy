# Java OOP

## 1. What is OOP?

OOP stands for **Object-Oriented Programming**.

OOP is a programming approach based on **classes and objects**.

Java is primarily an object-oriented programming language.

The four main pillars of OOP are:

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

Other important OOP concepts include:

- Class
- Object
- Constructor
- Interface
- Abstract Class
- `this`
- `super`
- `static`
- `final`
- Access Modifiers
- Association
- Aggregation
- Composition

---

# 2. Class

A **class** is a blueprint or template used to create objects.

Example:

    class Car {

        String color;
        String model;

        void drive() {
            System.out.println("Car is driving");
        }
    }

A class can contain:

- Variables
- Methods
- Constructors
- Blocks
- Nested classes

---

# 3. Object

An **object** is an instance of a class.

    Car car1 = new Car();

Here:

    Car       → Class
    car1      → Reference variable
    new Car() → Object

Example:

    class Car {

        String color;

        void drive() {
            System.out.println("Driving");
        }
    }

    public class Test {

        public static void main(String[] args) {

            Car car1 = new Car();

            car1.color = "Red";

            System.out.println(car1.color);

            car1.drive();
        }
    }

Output:

    Red
    Driving

---

# 4. Class vs Object

| Class | Object |
|---|---|
| Blueprint | Instance of a class |
| Logical entity | Runtime entity |
| Defines properties and behavior | Contains actual values |
| Example: `Car` | Example: `new Car()` |

---

# 5. Encapsulation

**Encapsulation** means wrapping data and methods together in a class and controlling access to the data.

Usually, variables are made `private` and accessed through public methods.

Example:

    class Employee {

        private String name;
        private int salary;

        public void setName(String name) {
            this.name = name;
        }

        public String getName() {
            return name;
        }

        public void setSalary(int salary) {
            this.salary = salary;
        }

        public int getSalary() {
            return salary;
        }
    }

Usage:

    Employee employee = new Employee();

    employee.setName("Selva");
    employee.setSalary(100000);

    System.out.println(employee.getName());
    System.out.println(employee.getSalary());

## Benefits of Encapsulation

- Data hiding
- Controlled access
- Better security
- Maintainability
- Validation
- Reduced coupling

Example:

    public void setSalary(int salary) {

        if (salary > 0) {
            this.salary = salary;
        }
    }

---

# 6. Inheritance

**Inheritance** allows one class to acquire properties and methods from another class.

The `extends` keyword is used.

Example:

    class Animal {

        void eat() {
            System.out.println("Eating");
        }
    }

    class Dog extends Animal {

        void bark() {
            System.out.println("Barking");
        }
    }

Usage:

    Dog dog = new Dog();

    dog.eat();
    dog.bark();

Output:

    Eating
    Barking

Here:

    Animal → Parent / Superclass
    Dog    → Child / Subclass

---

# 7. Types of Inheritance

Common types:

1. Single inheritance
2. Multilevel inheritance
3. Hierarchical inheritance
4. Multiple inheritance
5. Hybrid inheritance

Java supports through classes:

- Single inheritance
- Multilevel inheritance
- Hierarchical inheritance

Java does not support multiple inheritance through classes.

Multiple inheritance can be achieved using interfaces.

---

# 8. Single Inheritance

One parent and one child.

    class Animal {

        void eat() {
            System.out.println("Eating");
        }
    }

    class Dog extends Animal {

        void bark() {
            System.out.println("Barking");
        }
    }

Diagram:

    Animal
       |
      Dog

---

# 9. Multilevel Inheritance

Inheritance across multiple levels.

    class Animal {

        void eat() {
            System.out.println("Eating");
        }
    }

    class Dog extends Animal {

        void bark() {
            System.out.println("Barking");
        }
    }

    class Puppy extends Dog {

        void play() {
            System.out.println("Playing");
        }
    }

Diagram:

    Animal
       |
      Dog
       |
     Puppy

`Puppy` can access methods inherited from both `Dog` and `Animal`.

---

# 10. Hierarchical Inheritance

One parent and multiple children.

    class Animal {

        void eat() {
            System.out.println("Eating");
        }
    }

    class Dog extends Animal {

        void bark() {
            System.out.println("Barking");
        }
    }

    class Cat extends Animal {

        void meow() {
            System.out.println("Meowing");
        }
    }

Diagram:

           Animal
           /    \
         Dog    Cat

---

# 11. Multiple Inheritance

Java does not allow:

    class C extends A, B {
    }

This is not allowed with classes because it can create ambiguity.

Java supports multiple inheritance through interfaces.

Example:

    interface A {

        void methodA();
    }

    interface B {

        void methodB();
    }

    class C implements A, B {

        public void methodA() {
            System.out.println("A");
        }

        public void methodB() {
            System.out.println("B");
        }
    }

---

# 12. Polymorphism

Polymorphism means:

**One name, many forms.**

There are two major types:

1. Compile-time polymorphism
2. Runtime polymorphism

---

# 13. Method Overloading

Method overloading is **compile-time polymorphism**.

Multiple methods have the same name but different parameter lists.

Example:

    class Calculator {

        int add(int a, int b) {
            return a + b;
        }

        int add(int a, int b, int c) {
            return a + b + c;
        }

        double add(double a, double b) {
            return a + b;
        }
    }

Usage:

    Calculator calculator = new Calculator();

    System.out.println(calculator.add(10, 20));
    System.out.println(calculator.add(10, 20, 30));
    System.out.println(calculator.add(10.5, 20.5));

---

# 14. Rules for Method Overloading

Methods can be overloaded by changing:

- Number of parameters
- Type of parameters
- Order of parameter types

Example:

    void test(int a, String b) {
    }

    void test(String a, int b) {
    }

These are overloaded methods.

Changing only the return type is **not** enough.

Invalid:

    int test() {
        return 10;
    }

    String test() {
        return "Java";
    }

---

# 15. Method Overriding

Method overriding occurs when a child class provides its own implementation of a method inherited from the parent.

Example:

    class Animal {

        void sound() {
            System.out.println("Animal sound");
        }
    }

    class Dog extends Animal {

        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

Usage:

    Dog dog = new Dog();

    dog.sound();

Output:

    Dog barks

---

# 16. Runtime Polymorphism

Runtime polymorphism occurs through method overriding.

Example:

    class Animal {

        void sound() {
            System.out.println("Animal sound");
        }
    }

    class Dog extends Animal {

        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

Now:

    Animal animal = new Dog();

    animal.sound();

Output:

    Dog barks

The reference type is `Animal`, but the actual object is `Dog`.

The overridden method is selected at runtime.

---

# 17. Overloading vs Overriding

| Overloading | Overriding |
|---|---|
| Compile-time polymorphism | Runtime polymorphism |
| Usually within same class | Parent-child relationship |
| Parameters must differ | Parameters must match |
| Inheritance not required | Inheritance required |
| Return type alone cannot distinguish methods | Compatible return type required |

---

# 18. Abstraction

**Abstraction** means hiding implementation details and exposing only necessary functionality.

Java provides abstraction using:

1. Abstract classes
2. Interfaces

Example:

    abstract class Vehicle {

        abstract void start();

        void stop() {
            System.out.println("Vehicle stopped");
        }
    }

---

# 19. Abstract Class

A class declared using the `abstract` keyword is an abstract class.

Example:

    abstract class Animal {

        abstract void sound();

        void eat() {
            System.out.println("Eating");
        }
    }

An abstract class can contain:

- Abstract methods
- Concrete methods
- Variables
- Constructors
- Static methods
- Final methods

---

# 20. Abstract Method

An abstract method has no implementation in the abstract class.

    abstract void sound();

The child class must implement it unless the child class is also abstract.

Example:

    abstract class Animal {

        abstract void sound();
    }

    class Dog extends Animal {

        @Override
        void sound() {
            System.out.println("Bark");
        }
    }

---

# 21. Can We Create an Object of an Abstract Class?

No.

This is invalid:

    Animal animal = new Animal();

But we can create an abstract-class reference:

    Animal animal = new Dog();

This is also an example of runtime polymorphism.

---

# 22. Interface

An interface defines a contract that implementing classes must follow.

Example:

    interface Vehicle {

        void start();

        void stop();
    }

Implementation:

    class Car implements Vehicle {

        @Override
        public void start() {
            System.out.println("Car started");
        }

        @Override
        public void stop() {
            System.out.println("Car stopped");
        }
    }

---

# 23. Interface Methods

Modern Java interfaces can contain:

- Abstract methods
- Default methods
- Static methods
- Private methods

Example:

    interface Vehicle {

        void start();

        default void stop() {
            System.out.println("Stopping");
        }

        static void service() {
            System.out.println("Service");
        }
    }

---

# 24. Interface Variables

Variables declared in an interface are implicitly:

- `public`
- `static`
- `final`

Example:

    interface Constants {

        int MAX_SPEED = 120;
    }

Conceptually equivalent to:

    public static final int MAX_SPEED = 120;

---

# 25. Abstract Class vs Interface

| Abstract Class | Interface |
|---|---|
| Declared with `abstract class` | Declared with `interface` |
| Extended using `extends` | Implemented using `implements` |
| Can have instance variables | Variables are `public static final` |
| Can have constructors | Cannot have constructors |
| Can have concrete methods | Can have default/static/private methods |
| A class can extend only one class | A class can implement multiple interfaces |

---

# 26. Constructor

A constructor is used to initialize an object.

Characteristics:

- Same name as class
- No return type
- Called when object is created
- Can be overloaded

Example:

    class Employee {

        String name;

        Employee() {
            name = "Unknown";
        }
    }

Usage:

    Employee employee = new Employee();

    System.out.println(employee.name);

---

# 27. Parameterized Constructor

Example:

    class Employee {

        String name;
        int id;

        Employee(String name, int id) {

            this.name = name;
            this.id = id;
        }
    }

Usage:

    Employee employee =
            new Employee("Selva", 101);

---

# 28. Constructor Overloading

A class can have multiple constructors with different parameter lists.

    class Employee {

        Employee() {
            System.out.println("Default constructor");
        }

        Employee(String name) {
            System.out.println(name);
        }

        Employee(String name, int id) {
            System.out.println(name + " " + id);
        }
    }

---

# 29. Default Constructor

If you do not define any constructor, Java provides a default no-argument constructor.

Example:

    class Car {

        String color;
    }

Important:

Once you define your own constructor, Java does not automatically provide another no-argument constructor.

---

# 30. `this` Keyword

`this` refers to the current object.

Common uses:

1. Refer to current object's instance variable
2. Call another constructor in the same class
3. Call current class method
4. Pass current object as an argument
5. Return current object

Example:

    class Employee {

        String name;

        Employee(String name) {

            this.name = name;
        }
    }

Here:

    this.name

refers to the instance variable.

---

# 31. `this()` Constructor Call

`this()` calls another constructor in the same class.

Example:

    class Employee {

        Employee() {
            this("Unknown");
        }

        Employee(String name) {
            System.out.println(name);
        }
    }

Important:

`this()` must be the first statement in the constructor.

---

# 32. `super` Keyword

`super` refers to the immediate parent class.

Uses:

1. Access parent variable
2. Call parent method
3. Call parent constructor

Example:

    class Animal {

        String name = "Animal";
    }

    class Dog extends Animal {

        String name = "Dog";

        void printNames() {

            System.out.println(name);
            System.out.println(super.name);
        }
    }

Output:

    Dog
    Animal

---

# 33. `super()` Constructor

`super()` calls the parent class constructor.

Example:

    class Animal {

        Animal() {
            System.out.println("Animal constructor");
        }
    }

    class Dog extends Animal {

        Dog() {

            super();

            System.out.println("Dog constructor");
        }
    }

Output:

    Animal constructor
    Dog constructor

If you do not explicitly write `super()`, Java inserts a call to the accessible no-argument parent constructor when appropriate.

---

# 34. `static` Keyword

`static` means the member belongs to the class rather than an individual object.

Example:

    class Employee {

        static String company = "Toyota";

        String name;
    }

Access:

    System.out.println(Employee.company);

No object is required to access the static variable.

---

# 35. Static Method

Example:

    class Calculator {

        static int add(int a, int b) {

            return a + b;
        }
    }

Call:

    int result =
            Calculator.add(10, 20);

---

# 36. Static vs Instance

Example:

    class Employee {

        static String company = "Toyota";

        String name;
    }

Here:

    company → static → shared by the class
    name    → instance → belongs to each object

Example:

    Employee e1 = new Employee();
    Employee e2 = new Employee();

    e1.name = "Selva";
    e2.name = "John";

Each object has its own `name`.

Both objects can access the same static `company`.

---

# 37. Static Block

A static block executes when the class is initialized.

Example:

    class Test {

        static {

            System.out.println("Static block");
        }

        public static void main(String[] args) {

            System.out.println("Main");
        }
    }

Output:

    Static block
    Main

---

# 38. `final` Keyword

`final` can be used with:

- Variable
- Method
- Class

---

# 39. Final Variable

A final variable cannot be reassigned after initialization.

    final int MAX = 100;

This is invalid:

    MAX = 200;

---

# 40. Final Method

A final method cannot be overridden by a child class.

Example:

    class Parent {

        final void display() {

            System.out.println("Parent");
        }
    }

The child cannot override `display()`.

---

# 41. Final Class

A final class cannot be inherited.

Example:

    final class Vehicle {
    }

This is invalid:

    class Car extends Vehicle {
    }

A well-known example is:

    String

`String` is a final class.

---

# 42. Access Modifiers

Java provides four access levels:

1. `public`
2. `protected`
3. default
4. `private`

## public

Accessible from anywhere where the class is accessible.

    public String name;

## private

Accessible only within the same class.

    private String password;

## protected

Accessible within the same package and through inheritance in other packages, subject to Java's access rules.

    protected String name;

## default

No modifier.

Accessible within the same package.

    String name;

---

# 43. Access Modifier Table

| Modifier | Same Class | Same Package | Subclass | Other Package |
|---|---|---|---|---|
| `private` | Yes | No | No | No |
| default | Yes | Yes | Yes, if same package | No |
| `protected` | Yes | Yes | Yes | Yes, through inheritance |
| `public` | Yes | Yes | Yes | Yes |

---

# 44. Association

Association represents a relationship between two independent classes.

Example:

    Teacher ───── Student

A teacher and student can exist independently.

    class Teacher {
    }

    class Student {
    }

---

# 45. Aggregation

Aggregation represents a **HAS-A** relationship where the contained object can exist independently.

Example:

    Department
         |
         └── Teacher

A teacher can exist without a particular department.

Example:

    class Teacher {
    }

    class Department {

        Teacher teacher;

        Department(Teacher teacher) {
            this.teacher = teacher;
        }
    }

---

# 46. Composition

Composition is a stronger **HAS-A** relationship.

The contained object's lifecycle is strongly associated with the containing object.

Example:

    House
      |
      └── Room

Example:

    class Room {
    }

    class House {

        private Room room = new Room();
    }

---

# 47. Aggregation vs Composition

| Aggregation | Composition |
|---|---|
| Weak HAS-A relationship | Strong HAS-A relationship |
| Objects can exist independently | Lifecycle is strongly tied to owner |
| Department → Teacher | House → Room |

---

# 48. IS-A vs HAS-A

## IS-A

Represents inheritance.

    class Dog extends Animal {
    }

Dog **IS-A** Animal.

## HAS-A

Represents composition or aggregation.

    class Car {

        Engine engine;
    }

Car **HAS-A** Engine.

---

# 49. Selenium Example — Inheritance

A Selenium framework can use a base class.

    class BaseTest {

        void launchBrowser() {

            System.out.println("Browser launched");
        }
    }

    class LoginTest extends BaseTest {

        void login() {

            System.out.println("Login test");
        }
    }

Usage:

    LoginTest test = new LoginTest();

    test.launchBrowser();
    test.login();

`LoginTest` inherits `launchBrowser()` from `BaseTest`.

---

# 50. Selenium Example — Encapsulation

Page Object Model is a practical example of encapsulation.

    class LoginPage {

        private WebDriver driver;

        private By username =
            By.id("username");

        private By password =
            By.id("password");

        public LoginPage(WebDriver driver) {

            this.driver = driver;
        }

        public void enterUsername(String value) {

            driver.findElement(username)
                  .sendKeys(value);
        }

        public void enterPassword(String value) {

            driver.findElement(password)
                  .sendKeys(value);
        }
    }

The locators are hidden inside the class.

The test interacts through public methods:

    loginPage.enterUsername("Selva");
    loginPage.enterPassword("password");

This demonstrates **encapsulation**.

---

# 51. Selenium Example — Abstraction

A test can call:

    loginPage.login("Selva", "password");

without knowing the internal Selenium operations.

Example:

    public void login(String username, String password) {

        driver.findElement(usernameField)
              .sendKeys(username);

        driver.findElement(passwordField)
              .sendKeys(password);

        driver.findElement(loginButton)
              .click();
    }

The Selenium implementation details are hidden from the test.

This demonstrates **abstraction**.

---

# 52. Selenium Example — Polymorphism

Selenium uses the `WebDriver` interface.

    WebDriver driver;

The actual implementation can be:

    driver = new ChromeDriver();

or:

    driver = new FirefoxDriver();

or:

    driver = new EdgeDriver();

Conceptually:

    WebDriver
       |
       +---- ChromeDriver
       |
       +---- FirefoxDriver
       |
       +---- EdgeDriver

This is a real-world example of **runtime polymorphism**.

---

# 53. Four Pillars of OOP

## Encapsulation

    Hide data
    +
    Control access

Example:

    private String username;

---

## Inheritance

    Parent
       ↓
     Child

Example:

    class LoginTest extends BaseTest

---

## Polymorphism

    One name
    Many forms

Examples:

    Overloading
    Overriding

---

## Abstraction

    Hide implementation
    +
    Expose required functionality

Examples:

    Abstract class
    Interface

---

# 54. Easy Memory Trick

Remember:

    E → Encapsulation → Hide data
    I → Inheritance   → Reuse code
    P → Polymorphism  → Many forms
    A → Abstraction   → Hide implementation

    EIPA

---

# 55. Important OOP Keywords

    class
    object
    extends
    implements
    abstract
    interface
    this
    super
    static
    final
    private
    protected
    public

---

# 56. Common OOP Interview Questions

1. What is OOP?
2. What are the four pillars of OOP?
3. What is a class?
4. What is an object?
5. Class vs object?
6. What is encapsulation?
7. What is inheritance?
8. What types of inheritance does Java support?
9. Why doesn't Java support multiple inheritance through classes?
10. How can Java achieve multiple inheritance?
11. What is polymorphism?
12. What is compile-time polymorphism?
13. What is runtime polymorphism?
14. What is method overloading?
15. What is method overriding?
16. Overloading vs overriding?
17. What is abstraction?
18. Abstract class vs interface?
19. Can an abstract class have a constructor?
20. Can an interface have a constructor?
21. Can we create an object of an abstract class?
22. What is a constructor?
23. What is constructor overloading?
24. What is `this`?
25. What is `super`?
26. What is `static`?
27. What is `final`?
28. What are access modifiers?
29. What is IS-A relationship?
30. What is HAS-A relationship?
31. Association vs aggregation?
32. Aggregation vs composition?
33. Can a static method be overridden?
34. Can a private method be overridden?
35. Can a final method be overridden?
36. Can a constructor be inherited?
37. Can a constructor be overridden?
38. Why is String immutable?
39. How is OOP used in Selenium frameworks?
40. Explain OOP concepts using your Selenium framework.

---

# 57. Quick Interview Revision

| Concept | Meaning |
|---|---|
| Class | Blueprint |
| Object | Instance of class |
| Encapsulation | Data hiding + controlled access |
| Inheritance | Code reuse |
| Polymorphism | One name, many forms |
| Abstraction | Hide implementation details |
| Overloading | Same method name + different parameters |
| Overriding | Child provides its own implementation |
| Interface | Contract |
| Abstract class | Can contain abstract and concrete behavior |
| `this` | Current object |
| `super` | Parent class |
| `static` | Belongs to class |
| `final` | Cannot be changed/overridden/inherited depending on usage |
| IS-A | Inheritance |
| HAS-A | Association/Aggregation/Composition |

---

# 58. OOP in a Selenium Framework

A typical Selenium framework may look like:

    BaseTest
        ↓
    LoginTest
        ↓
    CheckoutTest

This demonstrates:

    Inheritance

Page classes:

    LoginPage
    HomePage
    CheckoutPage

encapsulate:

    Locators
    WebDriver operations
    Page actions

This demonstrates:

    Encapsulation

Interfaces and abstractions can define framework behavior:

    Browser
       ↓
    Chrome
    Firefox
    Edge

This demonstrates:

    Abstraction
    Polymorphism

Therefore, OOP is not just an interview topic. It is heavily used in real-world Selenium automation frameworks.

---

# 59. Final Summary

The most important OOP concepts for Java and Selenium interviews are:

1. Class
2. Object
3. Encapsulation
4. Inheritance
5. Polymorphism
6. Abstraction
7. Interface
8. Abstract Class
9. Constructor
10. Method Overloading
11. Method Overriding
12. `this`
13. `super`
14. `static`
15. `final`
16. Access Modifiers
17. Association
18. Aggregation
19. Composition
20. IS-A / HAS-A

For Selenium automation, focus especially on:

    OOP
      ↓
    Page Object Model
      ↓
    Base Test
      ↓
    Page Classes
      ↓
    Inheritance
      ↓
    Encapsulation
      ↓
    Abstraction
      ↓
    Polymorphism

These concepts form the foundation for a maintainable Java + Selenium + TestNG automation framework.
