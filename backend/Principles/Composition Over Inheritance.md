Why

-   Less coupling between classes.
-   Using inheritance, subclasses easily make assumptions, and break LSP.

How

-   Test for LSP (substitutability) to decide when to inherit.
-   Compose when there is a "has a" (or "uses a") relationship, inherit when "is a".

Resources

-   [Favor Composition Over Inheritance](https://blogs.msdn.microsoft.com/thalesc/2012/09/05/favor-composition-over-inheritance/)