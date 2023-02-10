Characteristics of a monolith

-   Deployed as a single unit
-   Single shared database
-   Communicate with synchronous method calls
-   Deep coupling between libaries and components(often through the db)
-   "big bang" style release(all or nothing release)
-   Long cycle times(weeks to months)
-   Teams carefully synchronize features and releases

Scaling a monolith
![[Pasted image 20230209221639.png]]
-   Multiple copies of the monolith are deployed
-   Each copy is independent. They don't communicate with each other
-   The database provides consistency between deployed instances


Advantages of a monolith

-   Easy cross module refactoring
	-   Changing dependencies can be done easy with idea tools
-   Easier to maintain consistency(db)
-   Single deployment process
-   Single thing to monitor
-   Simple scalability model

Disadvantages of a monolith

-   Limited by the maximum size of a single physical machine
-   Only scales as far as the database will allow
-   Components must be scaled as a group
-   Deep coupling leads to inflexibility
-   Development is typically slow(change is difficult, build times long)
-   Serious failure in one component brings down the whole monolith
	-   Redistribution of load can cause cascading failures
