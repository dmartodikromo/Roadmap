
A monolith, another architecture type associated with legacy systems, is a single application stack that contains all functionality within that 1 application. This is tightly coupled, both in the interaction between the services and how they are developed and delivered. 

Updating or scaling a single aspect of a monolithic application has implications for the entire application and its underlying infrastructure. 

A single change to the application code requires the whole application to be re-released. Because of this, updates and new releases typically can only occur once or twice per year, and may only include general maintenance instead of new features. 

In contrast, more modern architectures try to break out services by functionality or business capabilities to provide more agility.

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
