Abstract datatypes

Data structures is a way of organizing data so that it can be used effectively

Why data structures?

-   They are essential ingredients to creating fast and powerful algorithms
-   They help manage and organize data
-   They make code cleaner and easier to understand

Abstract data types vs data structures

An abstract data type (ADT) is an abstraction of a data structure which provides only the interface to which a data structure must adhere to.

The interface does not give any specific details about how something should be implemented or in what programming language

Examples
| Abstraction(ADT) | Implementation(DS)                                            |
| ---------------- | ------------------------------------------------------------- |
| List             | Dynamic array                                                 |
| Queue            | Linked list based queue, array based queue, stack based queue |
| Map              | Tree map, Hash map/Hash table                                 |
| Vehicle          | golf cart, bicycle, smart car                                 |

Introduction to Big-O

Complexity analysis

Questions that is always asked:

-   How much time does it take for this algorithm to finish
-   How much space does this algorithm need for its computation

Big-O notation gives an upper bound of the complexity in the worst case, helping to quantify performance as the input size becomes arbitrarily large

Big-O notation

N -  size of the input
Complexities ordered in from smallest to largest

| Time         | Notation    |
| ------------ | ----------- |
| Constant     | 0(1)        |
| Logarithmic  | 0(log(n))   |
| Linear       | 0(n)        |
| Linearithmic | 0(nlog(n))  |
| Quadratic    | 0(n^2)      |
| Cubic        | 0(n^3)      |
| Exponential  | 0(b^n), b>1 |
| Factorial    | 0(n!)       | 

Big-O properties
O(n + c) = O(n)
O(cn) = 0(n), c > 0
