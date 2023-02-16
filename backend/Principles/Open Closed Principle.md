Software entities (e.g. classes) should be open for extension, but closed for modification. I.e. such an entity can allow its behavior to be modified without altering its source code.

Why

-   Improve maintainability and stability by minimizing changes to existing code.

How

-   Write classes that can be extended (as opposed to classes that can be modified).
-   Expose only the moving parts that need to change, hide everything else.

Resources

-   [Open Closed Principle](https://en.wikipedia.org/wiki/Open/closed_principle)
-   [The Open Closed Principle](https://blog.cleancoder.com/uncle-bob/2014/05/12/TheOpenClosedPrinciple.html)