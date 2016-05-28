# Java Abstract Classes


We mentioned in [Java Interfaces](Java-Interfaces) that Interfaces do _NOT_ allow method bodies or default implementations (pre JDK 8). Guess what - Abstract Classes **allow** you to do so! However, you still can't instantiate an Abstract Class. 

Abstract classes need not necessarily have abstract methods. However, if all its methods are marked `abstract`, the class **must** be marked _abstract_.

#### What is an abstract method?

A method without a body (definition) is called **abstract method** and can be written as:

```java
abstract class AbstractClass{
	public abstract boolean areWeThereYet();
}

```

_Note_: The method name is terminated by a semicolon `;`. Even empty brackets `{}` would denote an empty method body and hence they aren't allowed.

_Can we instantiate this class?_ Nope. We'll get to that in the next section.

_Can it be subclassed?_ Yep. And that's the whole point. You **want** your subclass to _inherit_ some default behavior but it's free to override such behavior (methods). 

#### So, what's the big deal?

Think of Abstract classes as `incomplete classes` in the sense that they get **compiled** successfully, but are incomplete functionality wise. Additionally, they may or may not provide some default implementations (behavior). 

Note that `abstract` classes are NOT required to have any abstract methods. Don't believe me? The following Java code is perfectly legal:

```java

public abstract class AnotherAbstractClass {
    
    public void sayWhat(){};
    
}

```

**Abstract** classes can have a mixture of _abstract_ and _non-abstract_ methods.

```java


```



Now, to understand the possible usage of an `abstract` class, lets assume you are asked to design a class to represent a TV. One function of a TV is to display Volume Level. Also, assume that the default volume should be at level 10. So, we can design an **abstract** class as:

```java
abstract class UniversalTV{
	
	protected int defaultVolume = 10;
	
	void displayVolume(){
		System.out.println(defaultVolume);
	}
    
    ....//other methods not shown for conciseness
	
}
```

_Did you try to instantiate this class? If you did, you'd inevitably see the following_:

```java
Main.java:3: error: UniversalTV is abstract; cannot be instantiated
    UniversalTV universalTV = new UniversalTV();
                              ^
1 error
```

:rocket: [Run Code](https://repl.it/CWL9/1)

Ok - returning to our example - let's say the newest and coolest TV (codenamed AwesomeTV) follows this standard but has another button to _skip channels_! In order to comply with this, we can design **AwesomeTV** as:


```java
public class AwesomeTV extends UniversalTV{
	public void skipChannels(int n){
        System.out.println("Skipping "+ n +" channels");
    }
}

```

Let's try to run this using:

```java

class Main {
  public static void main(String[] args) {
   AwesomeTV tv = new AwesomeTV();
    tv.displayVolume();
    tv.skipChannels(7);
  }
}
```

You'll see the expected output:

```java
Volume:10
Skipping 7 channels
```

:rocket: [Run Code](https://repl.it/CWLf/0)

There are some interesting things to note here:

* **AwesomeTV** _inherits_ the default method `displayVolume` and hence we are able to use it.
* **AwesomeTV** is a _concrete_ class since it isn't marked `abstract`.
* **AwesomeTVRemote** is able to _add_ its own methods.

However, things get more interesting when we change the following line in `Main.java`:

```java
AwesomeTV tv = new AwesomeTV();
```

to:

```java
UniversalTV tv = new AwesomeTV();
```

Try to guess the output in this case and then check the actual result by running the code below.

(HINT: think `Polymorphism` and what does the variable **tv** point to at _runtime_? )

:rocket: [Run Code](https://repl.it/CWLg/0)


Continuing with our example of AwesomeTV, let's assume that the next super efficient model AwesomeTV_V2 needs to support default volume level 5.

Can you guess what we need to do in this case? If you answered **Override the `defaultVolume()` method** - Congrats!

```java
void displayVolume(){
    this.volume = 5;
    super.displayVolume();
}
```

#### Deja vu

All this while you might have been thinking are we really discussing **Abstract Classes** or have we been talking about **Interfaces** all along? Relax - you aren't the only one. With the introduction of default methods in JDK 8, the differences between an `Interface` and an `Abstract Class` has diminished further.  Choosing one over the other is mostly a design decision. 

#### So, what's the difference?

There are subtle differences between an **Abstract** class and an **Interface**. The most common ones to know are:

* A subclass can `extend` at most **one** Abstract class, whereas it may `implement` more than one Interface.
* The first concrete subclass of an Abstract class must define (i.e., provide a method body) **all abstract** methods. However, an abstract subclass need not define any of the inherited abstract methods.
* Interfaces can `extend` another Interface, and they need not define a method body. If parent interface and child interface have conflicting method signatures, a compilation error is raised in JDK 8.
* In an **Interface**, member variables are `public static final` by default, methods are  `public` by default. Specifying any other modifier such as private, protected results in compilation error. **Abstract** classes can, however, have properties with any visibility (private, protected, public).
* Consequently, subclasses can define **abstract** methods with _equal_ or _less visibility_ (as mandated by rules of Inheritence) whereas Interface method implementations are always `public`. 


#### When to use what

This is a tough one. A choice between these two is determined by the situation at hand. A rule of thumb is to use **abstract** classes if you want to promote _code re-useability_ whereas **interface** should be used in order to define a _contract_. In the real world, **interface** is widely used in design of Application Programming Interfaces (APIs). **Abstract** classes on the other hand are more suited for situations where the author of the class wants to keep the class extensible but provide some default implementation as well. A real example is the [Java ClassLoader](http://grepcode.com/file/repository.grepcode.com/java/root/jdk/openjdk/6-b14/java/lang/ClassLoader.java) - which is defined as an _abstract_ class and has been used by different corporations to provide ClassLoaders for their own version of Java / Web Application servers (e.g. IBM Websphere).
