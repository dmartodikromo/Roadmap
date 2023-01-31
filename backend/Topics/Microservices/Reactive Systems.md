## Why reactive?

Previous data was more rest -> data wasn't changing often
Current data -> constantly changing data

Size of installation. Database scripts -> technical problems
Problem that needs to be solved -> change in modern user expectation -> some users rely on critical services that can't be down for too long

Primary goal of reactive architecture -> provide an experience that is responsive under all conditions

What is a software landscape problem that reactive architecture is addressing?
The scale of modern systems far exceeds that of legacy systems, consisting of hundreds or even thousands of nodes.

Data At Rest:
The data is not consumed at the time it is injested. It is stored, and then consumed later in a batch process.

## The Goal

How can we build software that:

-   Scales from 10 to 10milion users
-   Consumes only necessary resources for current load(release or repurpose hardware when not used)
-   Handles failures with little ot no effect on the users
-   Can be distributed across a lot of machines
-   Maintains a consistent level of quality and responsiveness despite all of these things

## Reactive systems vs Reactive programming

-   Reactive systems and reactive programming are often misunderstood
-   Not equivalent
-   Reactive systems apply the reactive principles at the architectural level
-   Reactive programming can be used to build reactive systems or not

Reactive systems:

-   The reactive manifesto principles are intrinsic to the design and the architecture of the reactive systems
-   All major architectural components interact in a reactive way
-   Reactive systems are seperated along asynchronous boundaries
-   Reactive microservices

Reactive programming:

-   Reactive programming can be used to support the construction of reactive systems
-   Supports breaking problems into small, discrete steps
-   Steps are executed in an async/non-blocing fasion, usualy via a callback mechnanism
-   Futures/promises, streams, RxJava/RxScala
-   Systems that uses reactive programming is not necessarily a Reactive System

## Reactive systems and the actor model

The actor model:

-   The actor model is a programming paradigm that supports the construction of reactive systems
-   Message driven
-   Abstractioin provide elasticity and resilience
-   It can be used to build responsive software
-   On the JVM:
	-   Akka implements the actor model
	-   Akka is the foundation of Reactive tools like Lagom and Akka streams

Fundamental concepts of the actor model:
-   All computation occurs inside of the actors
-   Each actor has an adress
-   Actors communicate only through asynchronous messages

location transparency

```mermaid
flowchart TB
subgraph A
ActorA-->|Local|Router
Router-->|Local|ActorB
end
subgraph B
Router-->|Remote|ActorC
end
subgraph C
Router-->|Remote|ActorD
end
Location_transparency.->ActorA & ActorD
Resilient_and_elastic.->ActorC & ActorD
```
-   The message driven nature of actors supports location transparancy
-   Actors communicate using the same technique, regardless of location
-   Local vs remote is mostly configured
-   Location transparency enabled actors to be both resilient and elastic

Location transparancy vs transparent remoting:

Location transparancy should not be confused with transparent remoting
-   Transparent remoting:
	-   Remote calls look like local calls
	-   Hides the fact that you are making remote calls
	-   Hides potential failure scenarios(eg network failures)

-   Location transparency:
	-   Local calls look like remote calls
	-   Assumes you are always making remote calls
	-   You have to assume remote failure scenarios can occur(eg network failures)

Importance of the actor model:

-   There are many reactive programming tools
-   Most support only ome of the reactive principles
-   You often have to combine different technlogies to build a reactive system
-   The actor model provides facilities to support all of the reactive principles:
	- Message driven by default
	-   Location tranparency to support elasticity and resilience through distribution
	-   Elasticity and resilience provide responsiveness

Reactive system without actors
```mermaid
flowchart TB
Load_Balancer-->Service_1-->Service_Registry & Message_Bus
Load_Balancer-->Service_2-->Service_Registry & Message_Bus
Load_Balancer-->Service_3-->Service_Registry & Message_Bus
Load_Balancer-->Service_Registry
Location_Transparent.->Load_Balancer & Service_Registry
```

-   Reactive systems are possbile without using actors
-   Components are added on rather than being built in
-   Requires additional infrastructure as:
	-   Service registry
	-   Load balancer
	-   Message bus
-   Results will be reactive at the large scale, not necesaarily the small