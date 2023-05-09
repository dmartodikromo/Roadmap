
## Defining a class

```scala

// class without constructor
class User 
	val user1 = User()

// class with constructor
class Point(var x: Int, var y: Int): 

	def move(dx: Int, dy: Int): Unit = 
	x = x + dx 
	y = y + dy 
	
	override def toString: String = s"($x, $y)" 
	
end Point 
	
	val point1 = Point(2, 3) 
	println(point1.x) // prints 2 
	println(point1) // prints (2, 3)

// Constructors can have optional parameters by providing a default value

class Point(var x: Int = 0, var y: Int = 0) 
val origin = Point() // x and y are both set to 0 
val point1 = Point(1) // x is set to 1 and y is set to 0 
println(point1) // prints (1, 0)

class Point(var x: Int = 0, var y: Int = 0) 
val point2 = Point(y = 2) 
println(point2) // prints (0, 2)
```

We call the class like a function, as `User()`, to create an instance of the class. It is also possible to explicitly use the `new` keyword, as `new User()`, although that is usually left out.

Members are public by default. Use the `private` access modifier to hide them from outside of the class.

```scala
class Point: 

	private var _x = 0 
	private var _y = 0 
	private val bound = 100 
	
	def x: Int = _x 
	def x_=(newValue: Int): Unit = 
		if newValue < bound then 
			_x = newValue 
		else printWarning() 
		
	def y: Int = _y 
	
	def y_=(newValue: Int): Unit = 
		if newValue < bound then 
			_y = newValue 
		else printWarning() 
		
	private def printWarning(): Unit = 
		println("WARNING: Out of bounds") 
end Point 

val point1 = Point() 
point1.x = 99 
point1.y = 101 // prints the warning
```

Primary constructor parameters with `val` and `var` are public. However, because `val`s are immutable, you can’t write the following.

```scala
class Point(val x: Int, val y: Int) 
val point = Point(1, 2) 
point.x = 3 // <-- does not compile
```

Parameters without `val` or `var` are private values, visible only within the class.
```scala
class Point(x: Int, y: Int) 
val point = Point(1, 2) 
point.x // <-- does not compile
```