Separation of concerns is a design principle for separating a computer program into distinct sections, such that each section addresses a separate concern. For example the business logic of the application is a concern and the user interface is another concern. Changing the user interface should not require changes to business logic and vice versa.

Quoting [Edsger W. Dijkstra](https://en.wikipedia.org/wiki/Edsger_W._Dijkstra) (1974):

> It is what I sometimes have called "the separation of concerns", which, even if not perfectly possible, is yet the only available technique for effective ordering of one's thoughts, that I know of. This is what I mean by "focusing one's attention upon some aspect": it does not mean ignoring the other aspects, it is just doing justice to the fact that from this aspect's point of view, the other is irrelevant.

Why

-   Simplify development and maintenance of software applications.
-   When concerns are well-separated, individual sections can be reused, as well as developed and updated independently.

How

-   Break program functionality into separate modules that overlap as little as possible.

Resources

-   [Separation of Concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)