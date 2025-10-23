# Java Collections



| No   | Question                                                     |
| ---- | ------------------------------------------------------------ |
| 1    | [Collection Framework Hierarchy](#1)                         |
| 2    | [What is the difference between Collection and Collections in Java?](#2) |
| 3    | [What are the main interfaces in the Java Collections Framework?](#3) |
| 4    | [What is the difference between List, Set, and Map?](#4)     |
| 5    | [What are the differences between ArrayList and LinkedList?](#5) |
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

![Diagram](images/Untitled%20Diagram.drawio.png)

Java Collection class is one of the utility classes in java. The java.util package contains the Collections class in Java. The Java Collections class is used with the **static methods** that operate on the collections or return the collection. All the methods of this class throw a **NullPointerException** if the collection or object passed to the methods is null. 

```java
public class Collections extends Object // Inherited from Object
```



<h3 id="2">2. What is the difference between Collection and Collections in Java? </h3>

The main difference between `Collection` and `Collections` is, Collection is interface and Collections is a class.

###### Collection:

- It is the **root interface** of Collection Framework
- Almost all classes inherit from it.
- It defines basic operations such as insert, delete, size check, etc.

```java
Collection<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
System.out.println(names);
```

###### Collections:

- Its a **utility/helper class** that provides **static methods** for operating on collections
- **Common methods:**
  - `Collections.sort(list)`
  - `Collections.reverse(list)`
  - `Collections.shuffle(list)`
  - `Collections.unmodifiableList(list)`
  - `Collections.synchronizedList(list)`

```java
List<Integer> numbers = new ArrayList<>();
numbers.add(3);
numbers.add(1);
numbers.add(2);

Collections.sort(numbers); // Sorts the list
System.out.println(numbers); // [1, 2, 3]
```



<h3 id="3">3. What are the main interfaces in the Java Collections Framework? </h3>

The **Java Collections Framework (JCF)** defines a set of **interfaces**, **implementations (classes)**, and **algorithms (utility methods)** for working with groups of objects efficiently.

***Collection:*** [check here](#2)

***List:*** 

It is a**Ordered** collection (elements can be accessed by index) which allows **duplicate elements** and maintains **insertion order**.

**Common Implementations:**

- `ArrayList`
- `LinkedList`
- `Vector`
- `Stack`

```java
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
```

***Set:***

It is **UnOrdered collection** which does **not allow duplicates**. it is used when uniqueness is important.

**Common Implementations:**

- `HashSet`
- `LinkedHashSet`
- `TreeSet` (sorted order)

```java
Set<Integer> numbers = new HashSet<>();
numbers.add(1);
numbers.add(2);
numbers.add(1); // ignored
```

***Queue***:

It is used to **hold elements prior to processing** (FIFO – First In, First Out). Some queues (like `PriorityQueue`) order elements differently.

**Common Implementations:**

- `LinkedList`
- `PriorityQueue`
- `ArrayDeque`

```java
Queue<String> queue = new LinkedList<>();
queue.add("Task1");
queue.add("Task2");
queue.poll(); // removes and returns "Task1"
```

***Deque***:

It extends `Queue` to support **double-ended queues** (elements can be added/removed from both ends) also supports both **FIFO** and **LIFO** (stack-like) operations.

**Common Implementations:**

- `ArrayDeque`
- `LinkedList`

```java
Deque<String> deque = new ArrayDeque<>();
deque.addFirst("A");
deque.addLast("B");
```

***Map***:

It represents a **mapping of keys to values** (not part of the `Collection` hierarchy). Each key must be **unique**, but values can **repeat**.

```java
// Methods
put(), get(), remove(), containsKey(), keySet()
```

**Common Implementations:**

- `HashMap`
- `LinkedHashMap`
- `TreeMap`
- `Hashtable`
- `ConcurrentHashMap`

***SortedSet<E>** and **SortedMap<K, V>***:

It maintain elements/keys in **sorted order** (natural or custom `Comparator`). Subinterfaces of `Set` and `Map`, respectively.

**Common Implementations:**

- `TreeSet` → implements `SortedSet`
- `TreeMap` → implements `SortedMap`



| Interface    | Key Property       | Allows Duplicates?    | Ordered?            | Common Implementations        |
| ------------ | ------------------ | --------------------- | ------------------- | ----------------------------- |
| `Collection` | Root of all        | Depends on subtype    | Depends             | —                             |
| `List`       | Indexed, ordered   | Yes                   | Yes                 | `ArrayList`, `LinkedList`     |
| `Set`        | Unique elements    | No                    | No                  | `HashSet`, `TreeSet`          |
| `Queue`      | FIFO structure     | Yes                   | Yes                 | `LinkedList`, `PriorityQueue` |
| `Deque`      | Double-ended queue | Yes                   | Yes                 | `ArrayDeque`                  |
| `Map`        | Key-value pairs    | Keys: No, Values: Yes | Keys can be ordered | `HashMap`, `TreeMap`          |



<h3 id="4">4. What is the difference between List, Set, and Map? </h3>

In Java, **List**, **Set**, and **Map** are key interfaces in the **Collections Framework**, each serving a distinct purpose for storing and managing data.

A **List** is an **ordered collection** that allows **duplicate elements**. Elements can be accessed by their **index**, making it ideal when order matters or duplicates are needed. Common implementations include `ArrayList` (fast random access) and `LinkedList` (fast insertions/removals).

A **Set** is an **unordered collection** that **does not allow duplicates**. It is used when uniqueness of elements is required. The most common implementations are `HashSet` (fast access, no order) and `TreeSet` (elements sorted in natural or custom order).

A **Map** represents a collection of **key–value pairs** where each **key is unique**, but values can be duplicated. It allows quick lookups by key rather than by index. Common implementations include `HashMap` (unordered), `LinkedHashMap` (insertion order), and `TreeMap` (sorted keys).



<h3 id="5">5. What are the differences between ArrayList and LinkedList? </h3>

**ArrayList** is **backed by a dynamic array** (an `Object[]` array).
 When you create an `ArrayList`, Java internally creates a **resizable array** to store elements.
 If the array becomes full, a **new larger array** (usually 1.5 times bigger) is created and all elements are **copied** to it.

```java
List<String> list = new ArrayList<>();
list.add("A");
list.add("B");
```

> Internally: `[A, B, null, null, ...]` (capacity grows automatically)

**LinkedList** is **backed by a doubly linked list**.
 Each element (a **node**) holds the data plus references (links) to the **previous** and **next** nodes.
 When a new element is added, a **new node object** is created and linked to its neighbors—no resizing or copying required.

```java
List<String> list = new LinkedList<>();
list.add("A");
list.add("B");
```

> Internally: `A <-> B` (each node points to the previous and next)

| Operation                       | ArrayList                    | LinkedList                        |
| ------------------------------- | ---------------------------- | --------------------------------- |
| **Access (get/set)**            | Fast (O(1)) using index      | Slow (O(n)) — must traverse nodes |
| **Insertion/Deletion (middle)** | Slow (O(n)) — needs shifting | Fast (O(1)) once position known   |
| **Insertion/Deletion (end)**    | Fast (amortized O(1))        | Fast (O(1))                       |
| **Memory Usage**                | Less (just data)             | More (extra pointers per node)    |
