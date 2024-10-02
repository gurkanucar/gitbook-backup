# Java Shell & REPL

***

#### **What is REPL?**

**R**(ead) **E**(val) **P**(rint) **L**(oop), is an interactive programming environment that allows you to enter code snippets or expressions and immediately see the results of their evaluation.

This makes it easy to experiment and test out ideas by scripts.

**REPL**s are commonly used for scripting languages like Python, and JavaScript, but they can be used for any language that supports interactive evaluation of code such as **Java**, Kotlin, Clojure.

<figure><img src="https://cdn-images-1.medium.com/max/800/1*VzcYctx52vNKpIWRQqNxxA.png" alt=""><figcaption></figcaption></figure>

#### **REPL in Java**

With the release of Java 9, the Java development community was introduced to JShell, an official REPL tool that provides a streamlined and interactive way to write, test, and experiment with code snippets.

<figure><img src="https://cdn-images-1.medium.com/max/800/1*ADkQoiQyT2EPXIoCr5gCfQ.png" alt=""><figcaption></figcaption></figure>

#### **How to run JShell?**

To start JShell, enter the **jshell** command on the command line.

<figure><img src="https://cdn-images-1.medium.com/max/800/1*0V-FFGWFGrLqswksvWGwYQ.png" alt=""><figcaption></figcaption></figure>

#### **Useful JShell commands**

Enter the **/help** command on the command line to see details.

**/list =>** list the source you have typed

```
jshell> /list

   1 : import java.lang.String;
   2 : "Hello world!".toUpperCase().split(" ");
   3 : var a=5;
   4 : String name = "gurkan";
```

**/vars =>** list the declared variables and their values

```
jshell> /vars

|    String[] $3 = String[2] { "HELLO", "WORLD!" }
|    int a = 5
|    String name = "gurkan"
```

**/methods** => list the declared methods and their signatures

```
jshell> int sum(int x,int y){ return x+y;}

|  created method sum(int,int)

jshell> sum(10,20);
$9 ==> 30

jshell> /methods
|    int sum(int,int)
```

**/imports** => list the imported items

```
jshell> /imports

|    import java.io.*
|    import java.math.*
|    import java.lang.String
|    import java.util.*
```

**/exit** => to exit the jshell tool, ctrl+c won’t work!

```
jshell> /exit

|    Goodbye
```

#### Examples

<figure><img src="https://cdn-images-1.medium.com/max/800/1*Ozz-qIoH2k_D7a-YfsoaRQ.png" alt=""><figcaption><p><strong>Date-Time functions example</strong></p></figcaption></figure>

<figure><img src="https://cdn-images-1.medium.com/max/800/1*VJvollu_Pr1ERt6GjkHsOQ.png" alt=""><figcaption><p><strong>Class example</strong></p></figcaption></figure>

<figure><img src="https://cdn-images-1.medium.com/max/800/1*NQHEqLGjQBGsoQGqDEyCYw.png" alt=""><figcaption><p><strong>Streams example</strong></p></figcaption></figure>

***

#### Resources

[https://www.digitalocean.com/community/tutorials/java-repl-jshell](https://www.digitalocean.com/community/tutorials/java-repl-jshell)

[https://www.tutorialspoint.com/how-to-implement-java-time-localdate-using-jshell-in-java-9](https://www.tutorialspoint.com/how-to-implement-java-time-localdate-using-jshell-in-java-9)

[https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print\_loop](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print\_loop)

[https://docs.oracle.com/javase/10/jshell/introduction-jshell.htm](https://docs.oracle.com/javase/10/jshell/introduction-jshell.htm)

[https://www.infoworld.com/article/2971152/what-repl-means-for-java.htm](https://www.infoworld.com/article/2971152/what-repl-means-for-java.htm)[l](https://www.infoworld.com/article/2971152/what-repl-means-for-java.html)
