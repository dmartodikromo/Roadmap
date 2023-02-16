> Be conservative in what you do, be liberal in what you accept from others

Collaborating services depend on each others interfaces. Often the interfaces need to evolve causing the other end to receive unspecified data. A naive implementation refuses to collaborate if the received data does not strictly follow the specification. A more sophisticated implementation will still work ignoring the data it does not recognize.

Why

-   In order to be able to evolve services you need to ensure that a provider can make changes to support new demands while causing minimal breakage to their existing clients.

How

-   Code that sends commands or data to other machines (or to other programs on the same machine) should conform completely to the specifications, but code that receives input should accept non-conformant input as long as the meaning is clear.

Resources

-   [Robustness Principle in Wikipedia](https://en.wikipedia.org/wiki/Robustness_principle)
-   [Tolerant Reader](https://martinfowler.com/bliki/TolerantReader.html)