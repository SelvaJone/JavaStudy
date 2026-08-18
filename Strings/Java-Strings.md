# Java Strings

## 1. What is a String?

A `String` is a sequence of characters used to represent text in Java.

Example:

```java
String name = "Selva";
String company = "Toyota";
```

Strings are objects in Java and belong to the `java.lang` package. Therefore, `String` does not need to be explicitly imported.

```java
String message = "Hello Java";
```

---

# 2. Creating a String

There are two common ways to create a String.

## Using String Literal

```java
String name = "Java";
```

## Using new Keyword

```java
String name = new String("Java");
```

The String literal approach is generally preferred.

---

# 3. String Pool

Java maintains a special memory area called the **String Pool**.

When a String is created using a literal:

```java
String s1 = "Java";
String s2 = "Java";
```

Java can reuse the same String object from the String Pool.

Therefore:

```java
System.out.println(s1 == s2);
```

Output:

```text
true
```
## `==` vs `equals()`

This is one of the most important Java String interview questions.

### `==`

The `==` operator compares the **object references**, not the actual String contents.

Example:

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

Output:

```text
true
```

Why?

Both `"Java"` String literals are stored in the **String Pool**. Java reuses the same String object for the same literal.

Therefore:

```text
s1 ──────┐
         ├──> "Java"  (String Pool)
s2 ──────┘
```

Both variables refer to the same object, so:

```java
s1 == s2
```

returns:

```text
true
```

---

### `equals()`

The `equals()` method compares the **actual contents of the Strings**.

Example:

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1.equals(s2));
```

Output:

```text
true
```

Although `s1` and `s2` are two different objects, both contain the same text:

```text
s1 ───> "Java"
s2 ───> "Java"
```

Therefore:

```java
s1.equals(s2)
```

returns:

```text
true
```

---

### Important Difference

Now compare both operators:

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
```

Output:

```text
false
true
```

Why?

```text
==

Compares references
        ↓
Different objects
        ↓
false
```

```text
equals()

Compares contents
        ↓
Both contain "Java"
        ↓
true
```

### Easy Interview Rule

```text
==        → compares references
equals()  → compares contents
```

### Selenium Example

This is especially important in Selenium when comparing text returned from a web element.

Correct:

```java
String actualText = driver.findElement(By.id("message")).getText();

if (actualText.equals("Login Successful")) {
    System.out.println("Text matched");
}
```

Do **not** normally use:

```java
if (actualText == "Login Successful") {
}
```

because `==` compares references rather than String contents.


---

# 4. String Using new

When using `new`, a new String object is explicitly created.

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
```

Output:

```text
false
```

The objects are different even though their contents are the same.

---

# 5. == vs equals()

This is an important Java interview question.

## ==

The `==` operator compares object references.

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

Output:

```text
true
```

## equals()

`equals()` compares the actual String contents.

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1.equals(s2));
```

Output:

```text
true
```

### Remember

```text
==       → compares references
equals() → compares contents
```

---

# 6. String Immutability

Strings in Java are **immutable**.

Immutable means that once a String object is created, its contents cannot be changed.

Example:

```java
String name = "Java";

name.concat(" Selenium");

System.out.println(name);
```

Output:

```text
Java
```

The original String was not changed.

To store the new String:

```java
String name = "Java";

name = name.concat(" Selenium");

System.out.println(name);
```

Output:

```text
Java Selenium
```

A new String object is created.

---

# 7. Why is String Immutable?

String immutability provides several advantages:

* Security
* Thread safety
* String Pool optimization
* Hashcode caching
* Reliable use as a key in HashMap
* Safe sharing between different parts of an application

---

# 8. String length()

The `length()` method returns the number of characters.

```java
String name = "Selenium";

System.out.println(name.length());
```

Output:

```text
8
```

Important:

```java
array.length
```

For String:

```java
string.length()
```

For ArrayList:

```java
list.size()
```

---

# 9. charAt()

Returns the character at a specific index.

```java
String name = "Java";

System.out.println(name.charAt(0));
System.out.println(name.charAt(2));
```

Output:

```text
J
v
```

Indexes:

```text
J → 0
a → 1
v → 2
a → 3
```

---

# 10. StringIndexOutOfBoundsException

If an invalid index is accessed:

```java
String name = "Java";

System.out.println(name.charAt(10));
```

Java throws:

```text
StringIndexOutOfBoundsException
```

---

# 11. toUpperCase()

Converts a String to uppercase.

```java
String name = "selenium";

System.out.println(name.toUpperCase());
```

Output:

```text
SELENIUM
```

---

# 12. toLowerCase()

Converts a String to lowercase.

```java
String name = "SELENIUM";

System.out.println(name.toLowerCase());
```

Output:

```text
selenium
```

---

# 13. trim()

Removes leading and trailing spaces.

```java
String name = "   Selenium   ";

System.out.println(name.trim());
```

Output:

```text
Selenium
```

Note: `trim()` does not remove spaces between words.

---

# 14. strip()

`strip()` also removes leading and trailing whitespace.

```java
String name = "   Selenium   ";

System.out.println(name.strip());
```

`strip()` is Unicode-aware and is generally preferred over `trim()` when working with modern Java applications.

---

# 15. equals()

Compares two Strings for exact content equality.

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1.equals(s2));
```

Output:

```text
true
```

---

# 16. equalsIgnoreCase()

Compares Strings without considering uppercase/lowercase differences.

```java
String s1 = "Java";
String s2 = "JAVA";

System.out.println(s1.equalsIgnoreCase(s2));
```

Output:

```text
true
```

---

# 17. contains()

Checks whether a String contains a particular sequence of characters.

```java
String text = "Java Selenium Automation";

System.out.println(text.contains("Selenium"));
```

Output:

```text
true
```

---

# 18. startsWith()

Checks whether a String starts with a specified value.

```java
String text = "Selenium Automation";

System.out.println(text.startsWith("Selenium"));
```

Output:

```text
true
```

---

# 19. endsWith()

Checks whether a String ends with a specified value.

```java
String text = "Selenium Automation";

System.out.println(text.endsWith("Automation"));
```

Output:

```text
true
```

---

# 20. indexOf()

Returns the index of the first occurrence of a character or String.

```java
String text = "Java Selenium";

System.out.println(text.indexOf("Selenium"));
```

Output:

```text
5
```

If the value is not found:

```java
System.out.println(text.indexOf("Python"));
```

Output:

```text
-1
```

---

# 21. lastIndexOf()

Returns the index of the last occurrence.

```java
String text = "Java Java Selenium";

System.out.println(text.lastIndexOf("Java"));
```

---

# 22. substring()

Extracts part of a String.

```java
String text = "Java Selenium";

System.out.println(text.substring(5));
```

Output:

```text
Selenium
```

Using start and end indexes:

```java
System.out.println(text.substring(0, 4));
```

Output:

```text
Java
```

Important:

The ending index is **exclusive**.

```text
substring(0, 4)
         ↑  ↑
       start end
```

Characters at indexes `0, 1, 2, 3` are included.

---

# 23. replace()

Replaces characters or sequences.

```java
String text = "Java Selenium";

String result = text.replace("Java", "Python");

System.out.println(result);
```

Output:

```text
Python Selenium
```

---

# 24. replaceAll()

`replaceAll()` uses a regular expression.

```java
String text = "Java123Selenium456";

String result = text.replaceAll("[0-9]", "");

System.out.println(result);
```

Output:

```text
JavaSelenium
```

---

# 25. split()

Splits a String into an array.

```java
String text = "Java,Selenium,TestNG";

String[] values = text.split(",");

for (String value : values) {
    System.out.println(value);
}
```

Output:

```text
Java
Selenium
TestNG
```

---

# 26. concat()

Joins two Strings.

```java
String first = "Java";
String second = " Selenium";

String result = first.concat(second);

System.out.println(result);
```

Output:

```text
Java Selenium
```

The `+` operator can also concatenate Strings:

```java
String result = first + second;
```

---

# 27. isEmpty()

Checks whether the String has zero characters.

```java
String text = "";

System.out.println(text.isEmpty());
```

Output:

```text
true
```

---

# 28. isBlank()

Checks whether a String is empty or contains only whitespace.

```java
String text = "   ";

System.out.println(text.isBlank());
```

Output:

```text
true
```

Difference:

```text
isEmpty() → checks length == 0

isBlank() → checks empty or whitespace only
```

---

# 29. String to Character Array

Use `toCharArray()`.

```java
String text = "Java";

char[] chars = text.toCharArray();

for (char ch : chars) {
    System.out.println(ch);
}
```

Output:

```text
J
a
v
a
```

---

# 30. Convert Number to String

Using `String.valueOf()`:

```java
int number = 100;

String value = String.valueOf(number);

System.out.println(value);
```

Another approach:

```java
String value = Integer.toString(number);
```

---

# 31. Convert String to Integer

Use `Integer.parseInt()`.

```java
String value = "100";

int number = Integer.parseInt(value);

System.out.println(number);
```

If the String does not contain a valid integer:

```java
String value = "ABC";

int number = Integer.parseInt(value);
```

This causes:

```text
NumberFormatException
```

---

# 32. StringBuilder

`StringBuilder` is mutable.

Unlike String, its contents can be modified without creating a new String object for every operation.

Example:

```java
StringBuilder sb = new StringBuilder("Java");

sb.append(" Selenium");

System.out.println(sb);
```

Output:

```text
Java Selenium
```

---

# 33. StringBuilder Reverse

One of the easiest ways to reverse a String:

```java
String text = "Selenium";

String reverse = new StringBuilder(text)
                    .reverse()
                    .toString();

System.out.println(reverse);
```

Output:

```text
muineleS
```

---

# 34. StringBuilder Methods

Common methods:

```text
append()
insert()
delete()
deleteCharAt()
replace()
reverse()
length()
capacity()
```

Example:

```java
StringBuilder sb = new StringBuilder("Java");

sb.append(" Selenium");
sb.insert(0, "Learn ");

System.out.println(sb);
```

---

# 35. StringBuffer

`StringBuffer` is similar to `StringBuilder`, but its methods are synchronized.

```java
StringBuffer sb = new StringBuffer("Java");

sb.append(" Selenium");

System.out.println(sb);
```

### StringBuilder vs StringBuffer

| StringBuilder                            | StringBuffer                                 |
| ---------------------------------------- | -------------------------------------------- |
| Mutable                                  | Mutable                                      |
| Faster generally                         | Generally slower                             |
| Not synchronized                         | Synchronized                                 |
| Preferred for single-threaded operations | Useful where synchronized access is required |

---

# 36. String vs StringBuilder vs StringBuffer

| Feature                          | String     | StringBuilder            | StringBuffer             |
| -------------------------------- | ---------- | ------------------------ | ------------------------ |
| Mutable                          | No         | Yes                      | Yes                      |
| Thread-safe                      | Immutable  | No                       | Yes                      |
| Performance for repeated changes | Lower      | Better                   | Lower than StringBuilder |
| Typical use                      | Fixed text | Frequently changing text | Thread-safe mutable text |

---

# 37. Reverse a String Without StringBuilder

```java
String text = "Java";

String reverse = "";

for (int i = text.length() - 1; i >= 0; i--) {

    reverse = reverse + text.charAt(i);

}

System.out.println(reverse);
```

Output:

```text
avaJ
```

For repeated concatenation, `StringBuilder` is generally more efficient.

---

# 38. Check Palindrome

A palindrome reads the same forward and backward.

Examples:

```text
madam
level
radar
```

Example:

```java
String text = "madam";

String reverse = new StringBuilder(text)
                    .reverse()
                    .toString();

if (text.equals(reverse)) {

    System.out.println("Palindrome");

} else {

    System.out.println("Not Palindrome");

}
```

Output:

```text
Palindrome
```

---

# 39. Count Characters

```java
String text = "Selenium";

int count = 0;

for (int i = 0; i < text.length(); i++) {

    count++;

}

System.out.println("Character count = " + count);
```

---

# 40. Count Vowels

```java
String text = "Selenium".toLowerCase();

int count = 0;

for (int i = 0; i < text.length(); i++) {

    char ch = text.charAt(i);

    if (ch == 'a' ||
        ch == 'e' ||
        ch == 'i' ||
        ch == 'o' ||
        ch == 'u') {

        count++;
    }
}

System.out.println("Vowels = " + count);
```

---

# 41. Count Consonants

```java
String text = "Selenium".toLowerCase();

int count = 0;

for (int i = 0; i < text.length(); i++) {

    char ch = text.charAt(i);

    if (ch >= 'a' && ch <= 'z' &&
        ch != 'a' &&
        ch != 'e' &&
        ch != 'i' &&
        ch != 'o' &&
        ch != 'u') {

        count++;
    }
}

System.out.println("Consonants = " + count);
```

---

# 42. Find Duplicate Characters

```java
String text = "programming";

for (int i = 0; i < text.length(); i++) {

    for (int j = i + 1; j < text.length(); j++) {

        if (text.charAt(i) == text.charAt(j)) {

            System.out.println(
                "Duplicate = " + text.charAt(i)
            );

            break;
        }
    }
}
```

---

# 43. Character Frequency Using HashMap

This is an important interview problem.

```java
import java.util.HashMap;
import java.util.Map;

String text = "programming";

Map<Character, Integer> frequency = new HashMap<>();

for (char ch : text.toCharArray()) {

    frequency.put(
        ch,
        frequency.getOrDefault(ch, 0) + 1
    );
}

System.out.println(frequency);
```

Possible output:

```text
{p=1, r=2, o=1, g=2, a=1, m=2, i=1, n=1}
```

---

# 44. Find First Non-Repeated Character

```java
import java.util.LinkedHashMap;
import java.util.Map;

String text = "swiss";

Map<Character, Integer> frequency =
        new LinkedHashMap<>();

for (char ch : text.toCharArray()) {

    frequency.put(
        ch,
        frequency.getOrDefault(ch, 0) + 1
    );
}

for (Map.Entry<Character, Integer> entry :
        frequency.entrySet()) {

    if (entry.getValue() == 1) {

        System.out.println(
            "First non-repeated character = "
            + entry.getKey()
        );

        break;
    }
}
```

Output:

```text
w
```

`LinkedHashMap` preserves insertion order, which is useful when the first occurrence matters.

---

# 45. Check Anagram

Two Strings are anagrams if they contain the same characters with the same frequencies.

Example:

```text
listen
silent
```

Example:

```java
import java.util.Arrays;

String s1 = "listen";
String s2 = "silent";

char[] a = s1.toCharArray();
char[] b = s2.toCharArray();

Arrays.sort(a);
Arrays.sort(b);

if (Arrays.equals(a, b)) {

    System.out.println("Anagram");

} else {

    System.out.println("Not Anagram");

}
```

Output:

```text
Anagram
```

---

# 46. Remove Spaces

```java
String text = "Java Selenium Automation";

String result = text.replace(" ", "");

System.out.println(result);
```

Output:

```text
JavaSeleniumAutomation
```

---

# 47. Count Words

```java
String text = "Java Selenium TestNG";

String[] words = text.split(" ");

System.out.println("Word count = " + words.length);
```

Output:

```text
Word count = 3
```

For real-world input, consider trimming or splitting on whitespace using a regular expression:

```java
String[] words = text.trim().split("\\s+");
```

---

# 48. Reverse Each Word

```java
String text = "Java Selenium";

String[] words = text.split(" ");

String result = "";

for (String word : words) {

    result += new StringBuilder(word)
                .reverse()
                .toString();

    result += " ";
}

System.out.println(result.trim());
```

Output:

```text
avaJ muineleS
```

For better performance:

```java
StringBuilder result = new StringBuilder();

for (String word : words) {

    result.append(
        new StringBuilder(word).reverse()
    );

    result.append(" ");
}

System.out.println(result.toString().trim());
```

---

# 49. Remove Duplicate Characters

```java
String text = "programming";

String result = "";

for (int i = 0; i < text.length(); i++) {

    char ch = text.charAt(i);

    if (result.indexOf(ch) == -1) {

        result += ch;
    }
}

System.out.println(result);
```

Output:

```text
progamin
```

For larger Strings, a `LinkedHashSet` is generally a better approach.

---

# 50. String Coding Questions for Interviews

Practice these problems:

1. Reverse a String.
2. Check whether a String is a palindrome.
3. Count characters.
4. Count vowels.
5. Count consonants.
6. Count words.
7. Find duplicate characters.
8. Find character frequency.
9. Find the first non-repeated character.
10. Find the first repeated character.
11. Remove duplicate characters.
12. Check whether two Strings are anagrams.
13. Reverse each word.
14. Reverse the order of words.
15. Remove spaces.
16. Count uppercase characters.
17. Count lowercase characters.
18. Count numbers in a String.
19. Count special characters.
20. Find the longest word.
21. Find the shortest word.
22. Check whether a String contains only numbers.
23. Check whether a String contains only alphabets.
24. Replace duplicate characters.
25. Find the most frequently occurring character.

---

# 51. Important String Methods

Remember these methods:

```text
length()
charAt()
equals()
equalsIgnoreCase()
contains()
startsWith()
endsWith()
indexOf()
lastIndexOf()
substring()
replace()
replaceAll()
split()
concat()
trim()
strip()
isEmpty()
isBlank()
toUpperCase()
toLowerCase()
toCharArray()
```

---

# 52. Important StringBuilder Methods

```text
append()
insert()
delete()
deleteCharAt()
replace()
reverse()
length()
capacity()
```

---

# 53. Common String Exceptions

### StringIndexOutOfBoundsException

Occurs when an invalid String index is accessed.

```java
String text = "Java";

System.out.println(text.charAt(10));
```

### NumberFormatException

Occurs when an invalid String is converted to a number.

```java
String value = "ABC";

int number = Integer.parseInt(value);
```

---

# 54. Quick Interview Revision

```text
String
 ↓
Immutable
 ↓
String Pool
 ↓
== → reference comparison
equals() → content comparison
```

For frequently changing text:

```text
StringBuilder → mutable and generally faster
StringBuffer  → mutable and synchronized
```

Important concepts:

```text
String Pool
Immutability
StringBuilder
StringBuffer
equals()
==
substring()
split()
replace()
charAt()
```

---

# 55. Key Takeaway

For Java interviews, you should be comfortable with both **String concepts** and **String coding problems**.

The most important topics are:

* String immutability
* String Pool
* `==` vs `equals()`
* String vs StringBuilder vs StringBuffer
* String methods
* Reverse String
* Palindrome
* Duplicate characters
* Character frequency
* First non-repeated character
* Anagram
* Word manipulation
* Converting between String and numeric types
