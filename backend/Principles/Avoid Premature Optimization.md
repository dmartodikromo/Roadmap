Quoting [Donald Knuth](https://en.wikiquote.org/wiki/Donald_Knuth):

> Programmers waste enormous amounts of time thinking about, or worrying about, the speed of noncritical parts of their programs, and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%.

Understanding what is and isn’t "premature" is critical of course.

Why

-   It is unknown upfront where the bottlenecks will be.
-   After optimization, it might be harder to read and thus maintain.

How

-   [Make It Work Make It Right Make It Fast](http://wiki.c2.com/?MakeItWorkMakeItRightMakeItFast)
-   Don't optimize until you need to, and only after profiling you discover a bottleneck optimise that.

Resources

-   [Program optimization](https://en.wikipedia.org/wiki/Program_optimization)
-   [Premature Optimization](http://wiki.c2.com/?PrematureOptimization)