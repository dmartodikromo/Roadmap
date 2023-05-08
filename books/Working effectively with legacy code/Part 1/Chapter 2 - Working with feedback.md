
### What is unit testing

Unit tests are tests in isolation of the most atomic behavior of a system(classes, functions)

Advantages of testing in isolation in contrary to large tests:
-   Error localization
-   When testing large tests it is harder to pinpoint what the actual failing part is
-   Execution time
-   Small unit tests run faster than large tests
-   Coverage

A test is not a unit test when:
-   It talks to a database
-   It communicates across a network
-   It touches the file system
-   When special tasks are needed to run(configuration)

The legacy code dilemma
When we change code then we need to have tests, but when we need to put tests we need to change the code

### The legacy code change algorithm

Algorithm to change legacy code:

-   Identify change points
	-   If you don’t know your design well enough to feel that you are making changes in the right place, take a look at:
		-   Chapter 16, I Don’t Understand the Code Well Enough to Change It
		-   Chapter 17, My Application Has No Structure.

-   Find tests points
	-   finding places to write tests is easy, but in legacy code it can often be hard.  These chapters offer techniques that you can use to determine where you need to write your tests for particular changes:
		-   Chapter 11, I Need to Make a Change. What Methods Should I Test?
		-   Chapter 12, I Need to Make Many Changes in One Area. Do I Have to Break Dependencies for All the Classes Involved?

-   Break dependencies
	-   Dependencies are often the most obvious impediment to testing. The two ways this problem manifests itself are difficulty instantiating objects in test harnesses and difficulty running methods in test harnesses. Often in legacy code, you have to break dependencies to get tests in place. The following chapter shows some practices that can be used to make the first incisions in a system safer as you start to bring it under test:
		-   Chapter 23, How Do I Know That I’m Not Breaking Anything?
	-   For scenarios that show how to get past common dependency problems and these sections heavily reference the dependency breaking techniques located in chapter 25:
		-   Chapter 9, I can't get this class in a test harness
		-   Chapter 10, I Can’t Run This Method in a Test Harness
	-   Dependencies also show up when we have an idea for a test but we can’t write it easily. If you find that you can’t write tests because of dependencies in large methods:
		-   Chapter 22, I Need to Change a Monster Method and I Can’t Write Tests for It
	-   If you find that you can break dependencies, but it takes too long to build your tests check out the following chapter. This chapter describes additional dependency-breaking work that you can do to make your average build time faster:
		-   Chapter 7, It Takes Forever to Make a Change

-   Write tests
	-   I find that the tests I write in legacy code are somewhat different from the tests I write for new code. This chapter teaches you about the role of tests in legacy code:
		-   Chapter 13, I Need to Make a Change but I Don’t Know What Tests to Write
	
-   Make changes and refactor
	-   Use TDD when adding new features in legacy code. For a description of TDD and some other feature addition techniques:
		-   Chapter 8, How Do I Add a Feature?
	-   Techniques you can use to start to move your legacy code toward better structure:
		-   Chapter 20, This Class Is Too Big and I Don’t Want It to Get Any Bigger
		-   Chapter 21, I'm Changing the Same Code All Over the Place
		-   Chapter 22, I Need to Change a Monster Method and I Can’t Write Tests for It