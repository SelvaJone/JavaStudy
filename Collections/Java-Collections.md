# Java Collections

## 1. What is the Java Collections Framework?

The **Java Collections Framework (JCF)** is a set of interfaces, classes, and methods used to store and manipulate groups of objects.

Collections make it easier to:

* Store multiple objects
* Add and remove elements
* Search for elements
* Sort elements
* Iterate through data
* Remove duplicates
* Store key-value pairs

The main collection interfaces are:

```text
Collection
├── List
├── Set
└── Queue

Map
```

Important:

`Map` is part of the Java Collections Framework, but **Map does not extend the `Collection` interface**.

---

# 2. Collection Hierarchy

A simplified hierarchy:

```text
                    Iterable
                       |
                   Collection
                  /     |      \
                 /      |       \
              List     Set      Queue
               |        |         |
        ArrayList    HashSet    PriorityQueue
        LinkedList   LinkedHashSet
        Vector       TreeSet
        Stack

                    Map
                     |
          -------------------------
          |           |           |
       HashMap    LinkedHashMap  TreeMap
```

---

# 3. List

A `List` is an ordered collection.

Characteristics:

* Maintains insertion order
* Allows duplicate elements
* Allows index-based access
* Can contain multiple `null` values depending on implementation

Common implementations:

```text
ArrayList
LinkedList
Vector
Stack
```

Example:

```java
import java.util.ArrayList;
import java.util.List;

List<String> names = new ArrayList<>();

names.add("Java");
names.add("Selenium");
names.add("Java");

System.out.println(names);
```

Output:

```text
[Java, Selenium, Java]
```

Duplicates are allowed.

---

# 4. ArrayList

`ArrayList` is one of the most commonly used collection classes.

It uses a dynamically resizable array internally.

Example:

```java
import java.util.ArrayList;

ArrayList<String> names = new ArrayList<>();

names.add("Java");
names.add("Selenium");
names.add("TestNG");

System.out.println(names);
```

Output:

```text
[Java, Selenium, TestNG]
```

---

# 5. ArrayList Methods

## add()

```java
names.add("Java");
```

Adds an element to the end.

---

## add(index, element)

```java
names.add(1, "Selenium");
```

Adds an element at a specific index.

---

## get()

```java
System.out.println(names.get(0));
```

Gets an element by index.

---

## set()

```java
names.set(0, "Python");
```

Replaces an existing element.

---

## remove()

```java
names.remove(0);
```

Removes an element by index.

For an object:

```java
names.remove("Java");
```

---

## contains()

```java
System.out.println(names.contains("Selenium"));
```

Returns `true` if the element exists.

---

## size()

```java
System.out.println(names.size());
```

Returns the number of elements.

---

## isEmpty()

```java
System.out.println(names.isEmpty());
```

Returns `true` if the collection contains no elements.

---

## clear()

```java
names.clear();
```

Removes all elements.

---

# 6. ArrayList Example

```java
import java.util.ArrayList;

public class Test {

    public static void main(String[] args) {

        ArrayList<String> names = new ArrayList<>();

        names.add("Java");
        names.add("Selenium");
        names.add("TestNG");

        System.out.println(names.get(0));

        names.set(1, "Playwright");

        names.remove("TestNG");

        System.out.println(names);
    }
}
```

Output:

```text
Java
[Java, Playwright]
```

---

# 7. Loop Through ArrayList

## Normal for loop

```java
for (int i = 0; i < names.size(); i++) {

    System.out.println(names.get(i));

}
```

---

## Enhanced for loop

```java
for (String name : names) {

    System.out.println(name);

}
```

---

## forEach()

```java
names.forEach(name -> System.out.println(name));
```

---

# 8. LinkedList

`LinkedList` implements both `List` and `Deque`.

```java
import java.util.LinkedList;

LinkedList<String> names = new LinkedList<>();

names.add("Java");
names.add("Selenium");
names.add("TestNG");
```

It can be useful when frequent insertion and removal operations are required, especially at the ends of the list.

---

# 9. ArrayList vs LinkedList

| ArrayList                                | LinkedList                                   |
| ---------------------------------------- | -------------------------------------------- |
| Uses a dynamic array                     | Uses linked nodes                            |
| Fast random access                       | Slower random access                         |
| `get(index)` is efficient                | `get(index)` requires traversal              |
| Usually preferred for general list usage | Useful for frequent insert/remove operations |
| Less memory overhead per element         | More memory overhead per element             |

### Interview Point

For most everyday List use cases, **ArrayList is the default choice** unless you have a specific reason to use another implementation.

---

# 10. Set

A `Set` is a collection that does **not allow duplicate elements**.

Common implementations:

```text
HashSet
LinkedHashSet
TreeSet
```

Example:

```java
import java.util.HashSet;

HashSet<String> names = new HashSet<>();

names.add("Java");
names.add("Selenium");
names.add("Java");

System.out.println(names);
```

Output contains only one `"Java"`.

---

# 11. HashSet

`HashSet`:

* Does not allow duplicates
* Does not guarantee insertion order
* Allows one `null` element
* Uses hashing internally

Example:

```java
HashSet<Integer> numbers = new HashSet<>();

numbers.add(10);
numbers.add(20);
numbers.add(10);
numbers.add(30);

System.out.println(numbers);
```

Result contains:

```text
10
20
30
```

The displayed order should not be relied upon.

---

# 12. LinkedHashSet

`LinkedHashSet` maintains **insertion order** while preventing duplicates.

```java
import java.util.LinkedHashSet;

LinkedHashSet<String> names = new LinkedHashSet<>();

names.add("Java");
names.add("Selenium");
names.add("Java");
names.add("TestNG");

System.out.println(names);
```

Output:

```text
[Java, Selenium, TestNG]
```

---

# 13. TreeSet

`TreeSet` stores unique elements in **sorted order**.

```java
import java.util.TreeSet;

TreeSet<Integer> numbers = new TreeSet<>();

numbers.add(50);
numbers.add(10);
numbers.add(30);
numbers.add(20);

System.out.println(numbers);
```

Output:

```text
[10, 20, 30, 50]
```

---

# 14. HashSet vs LinkedHashSet vs TreeSet

| Feature         | HashSet        | LinkedHashSet          | TreeSet                      |
| --------------- | -------------- | ---------------------- | ---------------------------- |
| Duplicates      | No             | No                     | No                           |
| Insertion order | No guarantee   | Yes                    | No                           |
| Sorted order    | No             | No                     | Yes                          |
| Performance     | Generally fast | Slightly more overhead | Generally slower             |
| Null            | One null       | One null               | Usually does not permit null |

---

# 15. Map

A `Map` stores data as **key-value pairs**.

Example:

```text
Key       Value
101       Selva
102       John
103       David
```

Common implementations:

```text
HashMap
LinkedHashMap
TreeMap
Hashtable
```

Example:

```java
import java.util.HashMap;

HashMap<Integer, String> employees = new HashMap<>();

employees.put(101, "Selva");
employees.put(102, "John");
employees.put(103, "David");

System.out.println(employees);
```

---

# 16. HashMap

`HashMap`:

* Stores key-value pairs
* Does not guarantee insertion order
* Allows one `null` key
* Allows multiple `null` values
* Keys are unique

Example:

```java
HashMap<String, Integer> marks = new HashMap<>();

marks.put("Java", 90);
marks.put("Selenium", 95);
marks.put("TestNG", 85);

System.out.println(marks);
```

---

# 17. Duplicate Keys in HashMap

A `Map` cannot have duplicate keys.

Example:

```java
HashMap<Integer, String> employees = new HashMap<>();

employees.put(101, "Selva");
employees.put(102, "John");
employees.put(101, "David");

System.out.println(employees);
```

The second value for key `101` replaces the first value.

Result:

```text
101 → David
102 → John
```

---

# 18. HashMap Methods

## put()

```java
marks.put("Java", 90);
```

Adds a key-value pair.

---

## get()

```java
System.out.println(marks.get("Java"));
```

Returns the value associated with a key.

---

## containsKey()

```java
marks.containsKey("Java");
```

Checks whether a key exists.

---

## containsValue()

```java
marks.containsValue(90);
```

Checks whether a value exists.

---

## remove()

```java
marks.remove("Java");
```

Removes a key-value pair.

---

## size()

```java
marks.size();
```

Returns the number of entries.

---

## isEmpty()

```java
marks.isEmpty();
```

Checks whether the map is empty.

---

## clear()

```java
marks.clear();
```

Removes all entries.

---

# 19. Iterate Through HashMap

## Using keySet()

```java
for (Integer key : employees.keySet()) {

    System.out.println(key);
}
```

---

## Using values()

```java
for (String value : employees.values()) {

    System.out.println(value);
}
```

---

## Using entrySet()

This is commonly used when both key and value are required.

```java
for (Map.Entry<Integer, String> entry :
        employees.entrySet()) {

    System.out.println(
        entry.getKey() + " = " + entry.getValue()
    );
}
```

---

# 20. getOrDefault()

Very useful for counting frequencies.

```java
HashMap<String, Integer> frequency = new HashMap<>();

String[] values = {
    "Java",
    "Selenium",
    "Java"
};

for (String value : values) {

    frequency.put(
        value,
        frequency.getOrDefault(value, 0) + 1
    );
}

System.out.println(frequency);
```

Result:

```text
Java=2
Selenium=1
```

---

# 21. putIfAbsent()

Adds a value only if the key does not already exist.

```java
HashMap<Integer, String> employees = new HashMap<>();

employees.put(101, "Selva");

employees.putIfAbsent(101, "John");

System.out.println(employees.get(101));
```

Output:

```text
Selva
```

---

# 22. LinkedHashMap

`LinkedHashMap` maintains insertion order.

```java
import java.util.LinkedHashMap;

LinkedHashMap<Integer, String> employees =
        new LinkedHashMap<>();

employees.put(101, "Selva");
employees.put(102, "John");
employees.put(103, "David");

System.out.println(employees);
```

Output:

```text
{101=Selva, 102=John, 103=David}
```

---

# 23. TreeMap

`TreeMap` stores keys in sorted order.

```java
import java.util.TreeMap;

TreeMap<Integer, String> employees = new TreeMap<>();

employees.put(103, "David");
employees.put(101, "Selva");
employees.put(102, "John");

System.out.println(employees);
```

Output:

```text
{101=Selva, 102=John, 103=David}
```

---

# 24. HashMap vs LinkedHashMap vs TreeMap

| Feature         | HashMap           | LinkedHashMap   | TreeMap          |
| --------------- | ----------------- | --------------- | ---------------- |
| Key-value pairs | Yes               | Yes             | Yes              |
| Insertion order | No guarantee      | Yes             | No               |
| Sorted keys     | No                | No              | Yes              |
| Null key        | One               | One             | Generally no     |
| Performance     | Generally fastest | Slight overhead | Generally slower |

---

# 25. Queue

A `Queue` is generally used to process elements in a particular order.

A common behavior is **FIFO**:

```text
First In → First Out
```

Example:

```java
import java.util.LinkedList;
import java.util.Queue;

Queue<String> queue = new LinkedList<>();

queue.offer("Java");
queue.offer("Selenium");
queue.offer("TestNG");

System.out.println(queue);
```

---

# 26. Queue Methods

### offer()

Adds an element.

```java
queue.offer("Java");
```

### poll()

Removes and returns the first element.

```java
queue.poll();
```

### peek()

Returns the first element without removing it.

```java
queue.peek();
```

Example:

```java
Queue<String> queue = new LinkedList<>();

queue.offer("A");
queue.offer("B");
queue.offer("C");

System.out.println(queue.peek());
System.out.println(queue.poll());
System.out.println(queue);
```

Output:

```text
A
A
[B, C]
```

---

# 27. PriorityQueue

`PriorityQueue` processes elements according to their priority/order rather than simply preserving insertion order.

For natural ordering:

```java
import java.util.PriorityQueue;

PriorityQueue<Integer> numbers = new PriorityQueue<>();

numbers.offer(50);
numbers.offer(10);
numbers.offer(30);

System.out.println(numbers.poll());
```

Output:

```text
10
```

The smallest element has the highest priority under natural ordering.

---

# 28. Deque

`Deque` means **Double Ended Queue**.

Elements can be added or removed from both ends.

```java
import java.util.ArrayDeque;
import java.util.Deque;

Deque<String> deque = new ArrayDeque<>();

deque.addFirst("Java");
deque.addLast("Selenium");

System.out.println(deque);
```

Common methods:

```text
addFirst()
addLast()
offerFirst()
offerLast()
removeFirst()
removeLast()
peekFirst()
peekLast()
```

---

# 29. Stack

`Stack` represents a **LIFO** structure:

```text
Last In → First Out
```

Example:

```java
import java.util.Stack;

Stack<String> stack = new Stack<>();

stack.push("Java");
stack.push("Selenium");
stack.push("TestNG");

System.out.println(stack.pop());
```

Output:

```text
TestNG
```

For new code, `ArrayDeque` is generally preferred over the legacy `Stack` class for stack behavior.

---

# 30. Iterator

`Iterator` is used to traverse collection elements.

Example:

```java
import java.util.ArrayList;
import java.util.Iterator;

ArrayList<String> names = new ArrayList<>();

names.add("Java");
names.add("Selenium");
names.add("TestNG");

Iterator<String> iterator = names.iterator();

while (iterator.hasNext()) {

    System.out.println(iterator.next());
}
```

Important methods:

```text
hasNext()
next()
remove()
```

---

# 31. Removing Elements Using Iterator

An `Iterator` can safely remove elements during iteration.

```java
Iterator<String> iterator = names.iterator();

while (iterator.hasNext()) {

    String name = iterator.next();

    if (name.equals("Java")) {

        iterator.remove();
    }
}
```

This avoids the common problem of directly modifying a collection while iterating over it.

---

# 32. ConcurrentModificationException

This exception can occur when a collection is structurally modified while it is being iterated using an incompatible approach.

Example:

```java
ArrayList<String> names = new ArrayList<>();

names.add("Java");
names.add("Selenium");

for (String name : names) {

    if (name.equals("Java")) {

        names.remove(name);
    }
}
```

This can cause:

```text
ConcurrentModificationException
```

Use an `Iterator` when removal during iteration is required:

```java
Iterator<String> iterator = names.iterator();

while (iterator.hasNext()) {

    if (iterator.next().equals("Java")) {

        iterator.remove();
    }
}
```

---

# 33. Comparable

`Comparable` is used to define the **natural ordering** of objects.

It uses:

```java
compareTo()
```

Example:

```java
class Employee implements Comparable<Employee> {

    int id;

    Employee(int id) {
        this.id = id;
    }

    @Override
    public int compareTo(Employee other) {

        return this.id - other.id;
    }
}
```

Then:

```java
Collections.sort(employees);
```

---

# 34. Comparator

`Comparator` is used when you want to define a custom sorting rule.

Example:

```java
Comparator<Employee> byId =
    (e1, e2) -> Integer.compare(e1.id, e2.id);
```

Sorting:

```java
employees.sort(byId);
```

### Comparable vs Comparator

| Comparable                         | Comparator                           |
| ---------------------------------- | ------------------------------------ |
| `compareTo()`                      | `compare()`                          |
| Defines natural ordering           | Defines custom ordering              |
| Class itself implements Comparable | Separate Comparator can be created   |
| Usually one primary ordering       | Multiple sorting strategies possible |

---

# 35. Collections Utility Class

`Collections` is a utility class containing useful methods for working with collections.

Common methods:

```text
Collections.sort()
Collections.reverse()
Collections.shuffle()
Collections.max()
Collections.min()
Collections.frequency()
Collections.binarySearch()
```

Example:

```java
import java.util.ArrayList;
import java.util.Collections;

ArrayList<Integer> numbers = new ArrayList<>();

numbers.add(50);
numbers.add(10);
numbers.add(30);

Collections.sort(numbers);

System.out.println(numbers);
```

Output:

```text
[10, 30, 50]
```

---

# 36. Sorting in Reverse Order

```java
Collections.sort(
    numbers,
    Collections.reverseOrder()
);
```

Or:

```java
numbers.sort(Collections.reverseOrder());
```

---

# 37. Array vs ArrayList

| Array                              | ArrayList                             |
| ---------------------------------- | ------------------------------------- |
| Fixed size                         | Dynamic size                          |
| Primitive values supported         | Uses objects                          |
| `length`                           | `size()`                              |
| Faster for simple fixed structures | More flexible                         |
| Can use `Arrays` utility methods   | Can use `Collections` utility methods |

Example:

```java
int[] numbers = {10, 20, 30};
```

```java
ArrayList<Integer> numbers =
        new ArrayList<>();
```

---

# 38. Collection vs Collections

This is a common interview question.

### Collection

`Collection` is an **interface**.

```java
Collection<String> names =
        new ArrayList<>();
```

### Collections

`Collections` is a **utility class** containing static methods.

```java
Collections.sort(names);
```

Remember:

```text
Collection  → Interface
Collections → Utility class
```

---

# 39. Collection vs Map

| Collection                 | Map                                 |
| -------------------------- | ----------------------------------- |
| Stores individual elements | Stores key-value pairs              |
| List, Set, Queue           | HashMap, TreeMap, LinkedHashMap     |
| `add()` commonly used      | `put()` commonly used               |
| `contains()`               | `containsKey()` / `containsValue()` |

---

# 40. List vs Set

| List                                           | Set                                |
| ---------------------------------------------- | ---------------------------------- |
| Allows duplicates                              | Does not allow duplicates          |
| Maintains ordering depending on implementation | Ordering depends on implementation |
| Index-based access                             | No index-based access              |
| ArrayList, LinkedList                          | HashSet, LinkedHashSet, TreeSet    |

---

# 41. HashMap vs HashSet

A `HashSet` internally uses hashing to maintain unique elements.

A `HashMap` stores explicit key-value pairs.

```text
HashSet
Element
Element
Element
```

```text
HashMap
Key → Value
Key → Value
Key → Value
```

---

# 42. Common Collection Interview Questions

Practice these:

1. What is the Java Collections Framework?
2. What is the difference between List, Set, and Map?
3. ArrayList vs LinkedList?
4. HashSet vs LinkedHashSet vs TreeSet?
5. HashMap vs LinkedHashMap vs TreeMap?
6. HashMap vs Hashtable?
7. Array vs ArrayList?
8. Collection vs Collections?
9. List vs Set?
10. How does HashMap work?
11. Why can't a Map have duplicate keys?
12. Can HashMap contain null?
13. How do you iterate through a HashMap?
14. What is an Iterator?
15. Iterator vs ListIterator?
16. What is ConcurrentModificationException?
17. Comparable vs Comparator?
18. How do you sort an ArrayList?
19. How do you remove duplicates from a List?
20. How do you find duplicate elements?
21. How do you count element frequency?
22. How do you convert List to Set?
23. How do you convert Set to List?
24. How do you sort a Map by keys?
25. How do you sort a Map by values?

---

# 43. Common Coding Problems

## Remove Duplicates from a List

```java
import java.util.ArrayList;
import java.util.LinkedHashSet;

ArrayList<Integer> numbers =
        new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(10);
numbers.add(30);
numbers.add(20);

LinkedHashSet<Integer> unique =
        new LinkedHashSet<>(numbers);

System.out.println(unique);
```

Output:

```text
[10, 20, 30]
```

---

# 44. Find Duplicate Elements Using Set

```java
import java.util.HashSet;
import java.util.Set;

int[] numbers = {
    10, 20, 30, 20, 40, 10
};

Set<Integer> unique = new HashSet<>();

for (int number : numbers) {

    if (!unique.add(number)) {

        System.out.println(
            "Duplicate = " + number
        );
    }
}
```

Output:

```text
Duplicate = 20
Duplicate = 10
```

---

# 45. Count Frequency Using HashMap

```java
import java.util.HashMap;
import java.util.Map;

int[] numbers = {
    10, 20, 10, 30, 20, 10
};

Map<Integer, Integer> frequency =
        new HashMap<>();

for (int number : numbers) {

    frequency.put(
        number,
        frequency.getOrDefault(number, 0) + 1
    );
}

System.out.println(frequency);
```

Output:

```text
{10=3, 20=2, 30=1}
```

---

# 46. Find the Most Frequent Element

```java
Map<Integer, Integer> frequency =
        new HashMap<>();

for (int number : numbers) {

    frequency.put(
        number,
        frequency.getOrDefault(number, 0) + 1
    );
}

int maxFrequency = 0;
int mostFrequent = 0;

for (Map.Entry<Integer, Integer> entry :
        frequency.entrySet()) {

    if (entry.getValue() > maxFrequency) {

        maxFrequency = entry.getValue();
        mostFrequent = entry.getKey();
    }
}

System.out.println(
    "Most frequent = " + mostFrequent
);
```

---

# 47. Convert Array to List

For an object array:

```java
String[] names = {
    "Java",
    "Selenium",
    "TestNG"
};

List<String> list =
        Arrays.asList(names);
```

For a primitive `int[]`, `Arrays.asList(intArray)` does **not** produce a `List<Integer>` of the individual numbers. Use a loop or streams instead.

Example with streams:

```java
int[] numbers = {10, 20, 30};

List<Integer> list =
        Arrays.stream(numbers)
              .boxed()
              .toList();
```

---

# 48. Convert List to Array

```java
List<String> names = new ArrayList<>();

names.add("Java");
names.add("Selenium");

String[] array =
        names.toArray(new String[0]);
```

---

# 49. Important Collection Methods

### List

```text
add()
add(index, element)
get()
set()
remove()
contains()
size()
isEmpty()
clear()
```

### Set

```text
add()
remove()
contains()
size()
isEmpty()
clear()
```

### Map

```text
put()
get()
remove()
containsKey()
containsValue()
keySet()
values()
entrySet()
getOrDefault()
putIfAbsent()
size()
clear()
```

### Queue

```text
offer()
poll()
peek()
```

---

# 50. Quick Revision

```text
List
 ↓
Ordered
 ↓
Duplicates allowed
 ↓
ArrayList
LinkedList
```

```text
Set
 ↓
Unique elements
 ↓
No duplicates
 ↓
HashSet
LinkedHashSet
TreeSet
```

```text
Map
 ↓
Key + Value
 ↓
Unique keys
 ↓
HashMap
LinkedHashMap
TreeMap
```

```text
Queue
 ↓
Process elements in queue order
 ↓
offer()
poll()
peek()
```

```text
Deque
 ↓
Both ends
 ↓
addFirst()
addLast()
removeFirst()
removeLast()
```

---

# 51. Most Important Interview Points

Remember these differences:

```text
Array
→ Fixed size

ArrayList
→ Dynamic size

List
→ Duplicates allowed

Set
→ Duplicates not allowed

Map
→ Key-value pairs

HashSet
→ No guaranteed order

LinkedHashSet
→ Insertion order

TreeSet
→ Sorted order

HashMap
→ No guaranteed order

LinkedHashMap
→ Insertion order

TreeMap
→ Sorted keys

Comparable
→ Natural ordering

Comparator
→ Custom ordering

Iterator
→ Traverses collection

Collections
→ Utility class
```

---

# 52. Selenium Relevance

Collections are extremely important in Selenium automation.

### Get multiple elements

```java
List<WebElement> elements =
    driver.findElements(By.tagName("a"));
```

Then:

```java
for (WebElement element : elements) {

    System.out.println(element.getText());

}
```

### Store window handles

Selenium returns window handles as a `Set<String>`:

```java
Set<String> windows =
    driver.getWindowHandles();
```

Then:

```java
for (String window : windows) {

    driver.switchTo().window(window);
}
```

### Store dropdown options

```java
List<WebElement> options =
    driver.findElements(
        By.cssSelector("select option")
    );
```

Collections are therefore used extensively in real Selenium frameworks.

---

# 53. Key Takeaway

For Java and Selenium interviews, the most important Collections topics are:

* List
* Set
* Map
* Queue
* ArrayList
* LinkedList
* HashSet
* LinkedHashSet
* TreeSet
* HashMap
* LinkedHashMap
* TreeMap
* Iterator
* Comparable
* Comparator
* Collections utility class
* Duplicate detection
* Frequency counting
* Sorting
* Collection conversions

A strong understanding of Collections is essential because Selenium, TestNG, API automation, and Java coding problems frequently use `List`, `Set`, and `Map`.
