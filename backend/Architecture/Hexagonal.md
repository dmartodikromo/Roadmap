
![[Pasted image 20230209215258.png]]
![[Pasted image 20230209215448.png]]

-   Also known as Ports and Adapters
-   An alternative to the layered or N-tier architecture
-   Domain is isolated to the center of the model, becomes the architectural focus
-   Ports are exposed as an API for the domain
-   Infrastructure contains adapters that map to the ports

-   Hexagonal architecture can be viewed as an onion
-   Domain is the center of the onion
-   API provides an interface to the domain. These are your ports
-   Infrastructure adapts incoming and outgoing traffic into the ports
-   Outer layers depend on inner layers
-   Inner layers have no knowledge of outer layers

-   Hexagonal architecture ensures proper separation of infrastructure from domain
-   Prevents concerns around databases, user interfaces etc from bleeding into the domain
-   Can be enforced with package, or even project structure in the application
-   Allows your domain to be portable
	-   Easier to swap out infrastructure