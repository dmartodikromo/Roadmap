Cohesion of a single module/component is the degree to which its responsibilities form a meaningful unit; higher cohesion is better.

Why

-   Increased difficulty in understanding modules.
-   Increased difficulty in maintaining a system, because logical changes in the domain affect multiple modules, and because changes in one module require changes in related modules.
-   Increased difficulty in reusing a module because most applications won’t need the random set of operations provided by a module.

How

-   Group related functionalities sharing a single responsibility (e.g. in a class).

Resources

-   [Cohesion](https://en.wikipedia.org/wiki/Cohesion_(computer_science))
-   [Coupling And Cohesion](http://wiki.c2.com/?CouplingAndCohesion)