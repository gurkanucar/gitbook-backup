# Java Non-Access Modifiers

<figure><img src="../.gitbook/assets/image (2).png" alt="" width="375"><figcaption></figcaption></figure>

We’re familiar with access modifiers however, have you ever heard of Java’s non-access modifiers?

**abstract** — This modifier is used to create an abstract class or method that cannot be instantiated directly. An abstract class must be extended by a subclass that provides concrete implementations of its abstract methods.

**final**: This modifier is used to create a constant variable, method, or class. If a variable is defined as final, it cannot be changed after initialization. If a method is final, it cannot be overridden, also final classes cannot be extended by any subclass.

**static** — This modifier is used to create a class-level variable or method. Static members can be accessed without creating an object of the class.

**synchronized**: This modifier is used to make a method thread-safe by ensuring that only one thread can access it at a time.

**volatile**: This modifier is used to indicate that a variable is stored in main memory, so it’s read and written from/to main memory instead of the CPU cache.

**transient**: If you don’t want to serialize a variable you should use this. Transient variables are typically used for temporary or non-persistent data.

**strictfp** — This modifier guarantees the same floating-point calculations in any environment. Useful for precise calculations in financial or scientific applications.

**native** — This modifier indicates that a method will be implemented in languages other than Java (e.g., C, C++).

***

**resource:**

[https://javagyansite.com/2020/03/21/non-access-modifiers](https://javagyansite.com/2020/03/21/non-access-modifiers)

[https://www.educba.com/non-access-modifiers-in-java](https://www.educba.com/non-access-modifiers-in-java)
