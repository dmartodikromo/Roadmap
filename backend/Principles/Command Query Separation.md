The Command Query Separation principle states that each method should be either a command that performs an action or a query that returns data to the caller but not both. Asking a question should not modify the answer.

With this principle applied the programmer can code with much more confidence. The query methods can be used anywhere and in any order since they do not mutate the state. With commands one has to be more careful.

Why

-   By clearly separating methods into queries and commands the programmer can code with additional confidence without knowing each method's implementation details.

How

-   Implement each method as either a query or a command
-   Apply naming convention to method names that implies whether the method is a query or a command

Resources

-   [Command Query Separation in Wikipedia](https://en.wikipedia.org/wiki/Command%E2%80%93query_separation)
-   [Command Query Separation by Martin Fowler](https://martinfowler.com/bliki/CommandQuerySeparation.html)