# Java Abstract Classes


We mentioned in [Java Interfaces](Java-Interfaces) that Interfaces do _NOT_ allow method bodies or default implementations. Guess what - Abstract Classes **allow** you to do so! However, you still can't instantiate an Abstract Class. 

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

For example, lets assume you are asked to design a class to represent a Universal Remote control for a TV. A remote control has several buttons (some are programmable).Also, assume that the default volume should be at level 10. So, we can design an **abstract** class as:

```java
abstract class UniversalRemote{
	
	protected int defaultVolume = 10;
	
	void displayVolume(){
		System.out.println(volume);
	}
    
    ....
	
}
```

_Did you try to instantiate this class? If you did, you'd inevitably see the following_:

```java
Main.java:3: error: UniversalRemote is abstract; cannot be instantiated
    UniversalRemote universalRemote = new UniversalRemote();
                                      ^
1 error
```

:rocket: [Run Code](https://repl.it/CVJN/4)

Ok - returning to our example - let's say the newest and coolest TV remote(codenamed AwesomeTVRemote) follows this standard but has another button to _skip channels_! In order to comply with this, we can design **AwesomeTVRemote** as:


```java
public class AwesomeTVRemote extends UniversalRemote{
	public void skipChannels(int n){
        System.out.println("Skipping "+ n +" channels");
    }
}

```

Let's try to run this using:

```java

class Main{
  public static void main(String[] args) {
    AwesomeTVRemote remote = new AwesomeTVRemote();
    remote.displayVolume();
    remote.skipChannels(7);
    }
}
```

You'll see the expected output:

```java
Volume:10
Skipping 7 channels
```

:rocket: [Run Code](https://repl.it/CVKD/1)

There are some interesting things to note here:

* **AwesomeTVRemote** _inherits_ the default method `displayVolume` and hence we are able to use it.
* **AwesomeTVRemote** is a _concrete_ class since it isn't marked `abstract`.
* **AwesomeTVRemote** is able to _add_ its own methods.

However, things get more interesting when we change the following line in `Main.java`:

```java
AwesomeTVRemote remote = new AwesomeTVRemote();
```

to:

```java
UniversalRemote remote = new AwesomeTVRemote();
```

Try to guess the output in this case and then check the actual result by running the code below.

:rocket: [Run Code](https://repl.it/CVKY/0)


#### The best part

Continuing with our example of AwesomeTVRemote, let's assume that AwesomeTVRemoteV2 has decided no longer to support default volume of level 10. Instead, it supports level 5 as default volume. 

Can you guess what we need to do in this case? If you answered **Override the `defaultVolume()` method** - Congrats!

```java
void displayVolume(){
    this.volume = 5;
    super.displayVolume();
}
```

#### Deja vu

All this while you might have been thinking are we really discussing **Abstract Classes** or have we been talking about **Interfaces** all along? Breathe easy - you aren't the only one. With the introduction of default methods in JDK 8, the differences between an `Interface` and an `Abstract Class` has diminished further.  Choosing one over the other is a design decision. 

#### So, what's the difference?

Frankly there isn't much. However, some notable ones are:
