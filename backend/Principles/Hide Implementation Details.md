A software module hides information (i.e. implementation details) by providing an interface, and not leak any unnecessary information.

Why

-   When the implementation changes, the interface clients are using does not have to change.

How

-   Minimize accessibility of classes and members.
-   Don’t expose member data in public.
-   Avoid putting private implementation details into a class’s interface.
-   Decrease coupling to hide more implementation details.

Resources

-   [Information hiding](https://en.wikipedia.org/wiki/Information_hiding)