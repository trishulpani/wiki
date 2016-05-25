# Java Abstract Classes


We mentioned in [Java Interfaces](Java-Interfaces) that Interfaces do _NOT_ allow method bodies or default implementations. Guess what - Abstract Classes **allow** you to do so! However, you still can't instantiate an Abstract Class. 

#### So, what's the big deal?

Think of Abstract classes as `incomplete classes` in the sense that they get **compiled** successfully, but are incomplete functionality wise. 

For example, lets assume you are asked to design a class to represent an Universal Remote control for a TV. A remote control has a quite a few buttons. However, there are some common funtionalities - say increaase/decrease volume, change channel up/down - that are supported by all TVs. So, we can design an **abstract** class as:

```java
abstract class UniversalRemote{
	
	private int volume = 0;
	
	void increaseVolume(){
		volume++;
		System.out.println(volume);
	}
	
}
```

:rocket: [Run Code](https://repl.it/CVJN/0)