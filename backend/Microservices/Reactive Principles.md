the reactive manifesto -> [https://www.reactivemanifesto.org/](https://www.reactivemanifesto.org/)

The four basic principles of reactive systems:

1.  Responsive: consistenly responds in a timely fashion
2.  Resillient: Remains responsive even when failures occur
3.  Elastic: Remains responsive, despite changes to system load
4.  Message Driven: Built on a foundation of async, non-blocking messages

Responsive:

-   Cornerstone of usability
-   Must respond in a fast and consistent fashion of at all possible
-   Built for user confidence

Resilient:

-   Responsiveness despite failures
-   Achieved through replication(multiple copies), isolation(services van function on their own. No external dependencies), containment, delegation
-   Failures are isolated to a single component
-   Recovery is delegated to an external component
-   Failure brings down the whole system. Occurs frequently in monolithic aplications.

Elastic:

-   Provides responsiveness, despite increases or decreases in load
-   Zero contention and no central bottlenecks
-   Predictive auto scaling techniques can be used to support elasticity
-   Scaling up provides responsiveness during peak and scaling down improves cost effectiveneess

Message driven:

-   Responsive, resilience, elasticity are supported by a message driven architecture
-   Messages are asynchronous and non-blocking
-   Provides loos coupling, isolation, location transparancy
-   Resources are consumed only while active