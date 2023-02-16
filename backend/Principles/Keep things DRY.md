Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

Each significant piece of functionality in a program should be implemented in just one place in the source code. Where similar functions are carried out by distinct pieces of code, it is generally beneficial to combine them into one by abstracting out the varying parts.

Why

-   Duplication (inadvertent or purposeful duplication) can lead to maintenance nightmares, poor factoring, and logical contradictions.
-   A modification of any single element of a system does not require a change in other logically unrelated elements.
-   Additionally, elements that are logically related all change predictably and uniformly, and are thus kept in sync.

How

-   Put business rules, long expressions, if statements, math formulas, metadata, etc. in only one place.
-   Identify the single, definitive source of every piece of knowledge used in your system, and then use that source to generate applicable instances of that knowledge (code, documentation, tests, etc).
-   Apply the [Rule of three](https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming)).

Resources

-   [Dont Repeat Yourself](http://wiki.c2.com/?DontRepeatYourself)
-   [Don't repeat yourself](https://en.wikipedia.org/wiki/Don't_repeat_yourself)
-   [DRY Principle: Its Benefit and Cost with Examples](https://thevaluable.dev/dry-principle-cost-benefit-example/)

Related

-   [Abstraction principle](https://en.wikipedia.org/wiki/Abstraction_principle_(computer_programming))
-   [Once And Only Once](http://wiki.c2.com/?OnceAndOnlyOnce) is a subset of DRY (also referred to as the goal of refactoring).
-   [Single Source of Truth](https://en.wikipedia.org/wiki/Single_Source_of_Truth)
-   A violation of DRY is [WET](http://thedailywtf.com/articles/The-WET-Cart) (Write Everything Twice)
-   [Be careful with the code metric "duplicated lines"](https://rachelcarmena.github.io/2018/02/27/duplication-you-are-welcome.html)