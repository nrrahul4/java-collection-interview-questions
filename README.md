---
typora-copy-images-to: ./images/Untitled Diagram.drawio.png
typora-root-url: ./images/Untitled Diagram.drawio.png
---

# Java Collections



| No   | Question                                                     |
| ---- | ------------------------------------------------------------ |
| 1    | [Collection Framework Hierarchy](#1)                         |
| 2    | What is the difference between Collection and Collections in Java? |
| 3    | What are the main interfaces in the Java Collections Framework? |
| 4    | What is the difference between List, Set, and Map?           |
| 5    | What are the differences between ArrayList and LinkedList?   |
| 6    | What is the difference between HashSet and TreeSet?          |
| 7    | What is the difference between HashMap and Hashtable?        |
| 8    | How does HashMap work internally in Java?                    |
| 9    | What is the load factor in HashMap?                          |
| 10   | What is the difference between HashMap and TreeMap?          |
| 11   | When would you use ArrayList over LinkedList and vice versa? |
| 12   | Why is Set not allowed to have duplicate elements?           |
| 13   | What is the initial capacity of an ArrayList and how does it grow? |
| 14   | What are fail-fast and fail-safe iterators?                  |
| 15   | What is the difference between Iterator and ListIterator?    |
| 16   | How do you sort a List in Java?                              |
| 17   | What is the difference between Comparable and Comparator interfaces? |
| 18   | How can you make a collection thread-safe?                   |
| 19   | What are the concurrent collection classes in Java?          |
| 20   | What is the difference between synchronized collections and concurrent collections? |
|      |                                                              |



<h3 id="1">1. Collection Framework Hierarchy </h3>

![](/../Untitled Diagram.drawio.png)

Java Collection class is one of the utility classes in java. The java.util package contains the Collections class in Java. The Java Collections class is used with the **static methods** that operate on the collections or return the collection. All the methods of this class throw a **NullPointerException** if the collection or object passed to the methods is null. 

```java
public class Collections extends Object // Inherited from Object
```

