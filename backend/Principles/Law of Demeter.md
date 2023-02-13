Don't talk to strangers.

Why

-   It usually tightens coupling
-   It might reveal too much implementation details

How

A method of an object may only call methods of:

1.  The object itself.
2.  An argument of the method.
3.  Any object created within the method.
4.  Any direct properties/fields of the object.

Resources

-   [Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter)
-   [The Law of Demeter Is Not A Dot Counting Exercise](https://haacked.com/archive/2009/07/14/law-of-demeter-dot-counting.aspx/)