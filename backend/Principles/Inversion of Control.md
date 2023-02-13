nversion of Control is also known as the Hollywood Principle, "Don't call us, we'll call you". It is a design principle in which custom-written portions of a computer program receive the flow of control from a generic framework. Inversion of control carries the strong connotation that the reusable code and the problem-specific code are developed independently even though they operate together in an application.

Why

-   Inversion of control is used to increase modularity of the program and make it extensible.
-   To decouple the execution of a task from implementation.
-   To focus a module on the task it is designed for.
-   To free modules from assumptions about how other systems do what they do and instead rely on contracts.
-   To prevent side effects when replacing a module.

How

-   Using Factory pattern
-   Using Service Locator pattern
-   Using Dependency Injection
-   Using contextualized lookup
-   Using Template Method pattern
-   Using Strategy pattern

Resources

-   [Inversion of Control in Wikipedia](https://en.wikipedia.org/wiki/Inversion_of_control)
-   [Inversion of Control Containers and the Dependency Injection pattern](https://www.martinfowler.com/articles/injection.html)