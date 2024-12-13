# Java Core Refresher

This document serves as a refresher for key Java core topics, focusing on language features rather than specific classes or frameworks.

---

## 1. Interface vs. Abstract Class

| Feature                          | Interface                 | Abstract Class          |
|----------------------------------|---------------------------|-------------------------|
| **Constants (static final)**     | Yes (implied)             | Yes                     |
| **Static Variables**             | No                        | Yes                     |
| **Instance Variables**           | No                        | Yes                     |
| **Static Methods**               | No                        | Yes                     |
| **Method Definitions**           | No (implied public)       | Yes                     |
| **Constructors**                 | No                        | Yes                     |
| **Inheritance**                  | Only interfaces           | Classes/interfaces      |
| **Inner Classes/Interfaces**     | Static interfaces only    | Classes/interfaces      |

- **Key Point**: A class can extend only one abstract class but can implement multiple interfaces.

---

## 2. Overriding vs. Overloading

### Overriding
- Subclass provides a specific implementation for a method in the parent class.
- **Key Rules**:
  - Access modifier cannot be more restrictive.
  - Overriding method can throw fewer or no exceptions.

### Overloading
- Same method name, different parameter lists in the same class.
- Resolved at compile time.

---

## 3. Final Keyword

- **Class**: Prevents the class from being extended.
- **Method**: Prevents the method from being overridden.
- **Variable**:
  - Value cannot be changed after initialization.
  - Ensures thread-safe initialization.
  ```java
  final int x = 10; // Cannot reassign x
  ```

---

## 4. Arrays

### System.arraycopy
- For fast array copying.
- **Example**:
  ```java
  int[] src = {1, 2, 3};
  int[] dest = new int[3];
  System.arraycopy(src, 0, dest, 0, src.length);
  ```

### Array Polymorphism Issue
- **Example**:
  ```java
  class A {};
  class B extends A {};

  A[] array = new B[1];
  array[0] = new A(); // Throws ArrayStoreException
  ```

---

## 5. Conversions

### Primitive Operations
- Type of result depends on the operands.
- **Example**:
  ```java
  double result = 3 / 5; // Result is 0.0 because 3/5 is an integer operation.
  ```

### Type Casting
- **Example**:
  ```java
  int x = (int) 3.14; // Explicit cast
  double y = 10;      // Implicit cast
  ```


## 6. Autoboxing/Unboxing (JDK 5)
- Automatically converts between primitive types and their wrapper classes.
- **Examples**:
  ```java
  Integer x = 5; // Equivalent to Integer x = new Integer(5);
  Long y = 0L;
  for (; y < 25; y++) {}
  ```

---
## 6. Enums (JDK 5)
- Represent a fixed set of constants.
- **Example**:
  ```java
  public enum Test {
      TEST1, TEST2, TEST3
  }

  public void doIt(Test t) {
      switch (t) {
          case TEST1:
              System.out.println("Test1");
              break;
          default:
              System.out.println("Other Test");
      }
  }
  ```
- **Advanced Features**:
  - Enums can implement interfaces.
  - Abstract methods in enums can be overridden by constants.
  ```java
  public enum Operation {
      ADD {
          public int apply(int x, int y) { return x + y; }
      },
      SUBTRACT {
          public int apply(int x, int y) { return x - y; }
      };
      public abstract int apply(int x, int y);
  }
  ```

---



---

