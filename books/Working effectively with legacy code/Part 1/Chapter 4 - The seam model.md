
# Seams

A seam is a place where you can alter behavior in your program without editing in that place.

Why seams? What is this concept good for?
-   The seam view of software helps us see the opportunities that are already in the code base. If we can replace behavior at seams, we can selectively exclude dependencies in our tests. We can also run other code where those dependencies were if we want to sense conditions in the code and write tests against those conditions.

Seam -> a seam is a place where you can alter behavior in your program wihtout editing in that place

Enabling point -> Every seam has an enabling point, a place where you can make the decision to use one behavior or another.

The types of seams available to us vary among programming languages. The best way to explore them is to look at all of the steps involved in turning the text of a program into running code on a machine. Each identifiable step exposes different kinds of seams:
- preprocessing seams
- link seams
- object seams