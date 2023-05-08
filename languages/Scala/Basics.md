
## Expressions

### Values

- You can name the results of expressions using the `val` keyword
- values cannot be reassigned
- the type of a value can be omitted and inferred, or it can be explicitly stated

```scala
val x = 1 + 1
x = 3 // will not compile
val c: Int = 1 + 1 // explicit statement
```

### Variables

- Variables are like values, except you can re-assign them. You can define a variable with the `var` keyword
- As with values, the type of a variable can be omitted and inferred, or it can be explicitly stated

```scala
var x = 1 + 1
x = 3 // allowed
var c: Int = 1 + 1 // explicit statement
```

## Blocks

You can combine expressions by surrounding them with `{}`

```scala
println({ 
	val x = 1 + 1 
	x + 1 
}) // 3
```


## Functions

- You can define an anonymous function (i.e., a function that has no name) that returns a given integer plus one
-  On the left of `=>` is a list of parameters. On the right is an expression involving the parameters.

```scala
// anon function
(x: Int) => x + 1

// params and expression
val addOne = (x: Int) => x + 1
val add = (x: Int, y: Int) => x + y
val getTheAnswer = () => 42
```

## Methods

Methods look and behave very similar to functions, but there are a few key differences between them.

Methods are defined with the `def` keyword. `def` is followed by a name, parameter list(s), a return type, and a body:

```scala
def add(x: Int, y: Int): Int = x + y
def add(x: Int, y: Int): Int = {
	x + y
}
```

A method can take multiple parameter lists:

```scala
def addThenMultiply(x: Int, y: Int)(multiplier: Int): Int = (x + y) * multiplier

// calling
addThenMultiply(1,2)(3)
```

no parameter:

```scala
def name: String = System.getProperty("user.name")
```

## Classes

You can define classes with the `class` keyword, followed by its name and constructor parameters:

```scala
class Greeter(prefix: String, suffix: String): 
	def greet(name: String): Unit = 
		println(prefix + name + suffix)
```

The return type of the method `greet` is `Unit`, which signifies that there is nothing meaningful to return. It is used similarly to `void` in Java and C. (A difference is that, because every Scala expression must have some value, there is actually a singleton value of type Unit, written (). It carries no information.)

In Scala 2 you can make an instance of a class with the `new` keyword. In Scala 3, however, the `new` keyword is not needed thanks to [universal apply methods](https://docs.scala-lang.org/scala3/reference/other-new-features/creator-applications.html):

```scala
// scala 2
val greeter = new Greeter("Hello, ", "!") 
greeter.greet("Scala developer") // Hello, Scala developer!

// scala 3
val greeter = Greeter("Hello, ", "!") 
greeter.greet("Scala developer") // Hello, Scala developer!
```

## Case Classes

Scala has a special type of class called a “case” class. By default, instances of case classes are immutable, and they are compared by value (unlike classes, whose instances are compared by reference). This makes them additionally useful for [pattern matching](https://docs.scala-lang.org/tour/pattern-matching.html#matching-on-case-classes).

You can define case classes with the `case class` keywords:

```scala
case class Point(x: Int, y: Int)

// You can instantiate case classes without the `new` keyword:
val point = Point(1, 2) 
val anotherPoint = Point(1, 2) 
val yetAnotherPoint = Point(2, 2)

if point == anotherPoint then 
	println(s"$point and $anotherPoint are the same.") 
else 
	println(s"$point and $anotherPoint are different.") 
// ==> Point(1,2) and Point(1,2) are the same. 

if point == yetAnotherPoint then 
	println(s"$point and $yetAnotherPoint are the same.") 
else 
	println(s"$point and $yetAnotherPoint are different.") 
	// ==> Point(1,2) and Point(2,2) are different.
```

## Objects

Objects are single instances of their own definitions. You can think of them as singletons of their own classes.

You can define objects with the `object` keyword:

```scala
object IdFactory: 
	private var counter = 0 
	def create(): Int = 
	counter += 1 
	counter
```

You can access an object by referring to its name:

```scala
val newId: Int = IdFactory.create() 
println(newId) // 1 
val newerId: Int = IdFactory.create() 
println(newerId) // 2
```

## Traits

Traits are abstract data types containing certain fields and methods. In Scala inheritance, a class can only extend one other class, but it can extend multiple traits.

You can define traits with the `trait` keyword:

```scala
trait Greeter: def greet(name: String): Unit

// Traits can also have default implementations:
trait Greeter: 
	def greet(name: String): Unit = 
		println("Hello, " + name + "!")

// You can extend traits with the `extends` keyword and override an implementation with // the `override` keyword:

class DefaultGreeter extends Greeter 

class CustomizableGreeter(prefix: String, postfix: String) extends Greeter: 
	override def greet(name: String): Unit = 
		println(prefix + name + postfix) 
	
	val greeter = DefaultGreeter() 
	greeter.greet("Scala developer") 
	// Hello, Scala developer! 
	
	val customGreeter = CustomizableGreeter("How are you, ", "?")
	customGreeter.greet("Scala developer") 
	// How are you, Scala developer?
```

## Program entrypoint

In Scala 3, with the `@main` annotation, a main method is automatically generated from a method as follows:

```scala
@main def hello() = println("Hello, Scala developer!")
```