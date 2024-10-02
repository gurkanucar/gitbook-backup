# Functional Interfaces

Java functional interfaces are interfaces with a single abstract method, often used in lambda expressions or method references. They are a core part of functional programming in Java.

* **Consumer**: Accepts an argument and performs an action without returning a result.

```java
  public static Consumer<String> printConsumer =
      value -> System.out.println(value); // Takes args, don't return anything
```

* **Predicate**: Evaluates an argument and returns a boolean value (`true` or `false`).

```java
  public static Predicate<String> isFirstLetterUpperCase =
      value -> Character.isUpperCase(value.charAt(0)); // Takes args, returns just True|False
```

* **Function**: Accepts an argument and returns a result.

```java
  public static Function<String, String> convertToUpperCase =
      value -> value.toUpperCase(); // Takes args, returns values
```

* **Supplier**: Provides a result without taking any arguments.

```java
  public static Supplier<List<String>> getData
      = () -> List.of("gurkan", "Metin", "ali", "Sezai"); // Don't take args, returns values

```

Result:

```java
  public static void main(String[] args) {
    getData.get().stream()
        .filter(isFirstLetterUpperCase)
        .map(convertToUpperCase)
        .forEach(printConsumer);
  }
  // output:
  // METIN
  // SEZAI
```
