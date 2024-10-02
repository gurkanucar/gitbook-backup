# Java & Maven Commands

#### **Java Commands**

1.  **Compile a Java file**:

    ```bash
    javac MyClass.java
    ```
2.  **Run a compiled Java class**:

    ```bash
    java MyClass
    ```
3.  **Run a JAR file**:

    ```bash
    java -jar myapp.jar
    ```
4.  **Set classpath for external libraries**:

    ```bash
    java -cp .:path_to_lib/library.jar MyClass
    ```
5.  **Check Java version**:

    ```bash
    java -version
    ```

#### **Maven Commands**

1.  **Create a new Maven project**:

    ```bash
    mvn archetype:generate
    ```
2.  **Clean the target directory (remove generated files)**:

    ```bash
    mvn clean
    ```
3.  **Compile the source code**:

    ```bash
    mvn compile
    ```
4.  **Run unit tests**:

    ```bash
    mvn test
    ```
5.  **Package the project (create a JAR or WAR file)**:

    ```bash
    mvn package
    ```
6.  **Clean and build the project**:

    ```bash
    mvn clean install
    ```
7.  **Run a specific goal**:

    ```bash
    mvn goal_name
    ```

    Example:

    ```bash
    mvn install
    ```
8.  **Skip tests during build**:

    ```bash
    mvn clean install -DskipTests
    ```
9.  **Run a Spring Boot application using Maven**:

    ```bash
    mvn spring-boot:run
    ```
10. **Check for updates of dependencies**:

    ```bash
    mvn versions:display-dependency-updates
    ```

#### **Spring Boot Commands**

1.  **Run a Spring Boot application (if packaged as a JAR)**:

    ```bash
    java -jar target/myapp.jar
    ```
2.  **Run Spring Boot application directly from source**:

    ```bash
    mvn spring-boot:run
    ```
3.  **Generate a Spring Boot project** using the Spring Initializer:

    ```bash
    curl https://start.spring.io/starter.zip -d dependencies=web -o demo.zip
    ```
4.  **Clean and build Spring Boot application**:

    ```bash
    mvn clean package
    ```
5.  **Create a Spring Boot executable JAR**:

    ```bash
    mvn clean package
    ```
6.  **Run a Spring Boot application with an active profile**:

    ```bash
    java -jar target/myapp.jar --spring.profiles.active=dev
    ```
7.  **Check Spring Boot version**:

    ```bash
    mvn dependency:tree | grep spring-boot
    ```
8.  **Run with debugging enabled**:

    ```bash
    mvn spring-boot:run -Dspring-boot.run.fork=false -X
    ```
