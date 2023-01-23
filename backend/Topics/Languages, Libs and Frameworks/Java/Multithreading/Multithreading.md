When we run a real-world application, we use good processors for faster execution. But, only processor speed can’t make your application run fast. One of the great ways to create a performance efficient application is use utilize multithreading.

# What is multithreading

Multithreading is a programming concept in which the application can create a small unit of tasks to execute in parallel. A thread is a lightweight sub-process, the smallest unit of processing. If you are working on a computer, it runs multiple applications and allocates processing power to them.

# Why Multithreading

common reasons:
- Better utilization of a single cpu
- Better utilization of multiple CPUs or CPU cores.
- Better user experience with regards to responsiveness.
- Better user experience with regards to fairness.

# JVM and threads

there is no limit of threads that the JVM can make. the limiting factor is the underlying hardware the application is ran on

# Multithreading vs Multiprocessing

both mutlithreading and multiprocessing is used to achieve multitasking(executing multiple tasks simultaniously)

difference between multithreading and multiprocessing

- multiprocessing
multiprocessing refers to the ability of a system to have more than one CPU or processor core, each of which can execute threads concurrently. This allows a program to perform multiple tasks concurrently across multiple CPUs or processor cores.

- multithreading
multithreading is used to improve the performance of a program by allowing it to perform multiple tasks concurrently within a single program, while multiprocessing is used to improve the performance of a program by allowing it to use multiple CPUs or processor cores to execute tasks concurrently. 

only switch from singlethreaded applications to multithreaded ones if the benefits greately outweigh the costs. threads accessing shared data need special attention. incorrect thread synchronization can be very hard to detect, reproduce and fix.

When a CPU switches from executing one thread to executing another, the CPU needs to save the local data, program pointer etc. of the current thread, and load the local data, program pointer etc. of the next thread to execute. This switch is called a "context switch". The CPU switches from executing in the context of one thread to executing in the context of another.

Context switching isn't cheap. You don't want to switch between threads more than necessary.

A thread needs some resources from the computer in order to run. Besides CPU time a thread needs some memory to keep its local stack. It may also take up some resources inside the operating system needed to manage the thread. Try creating a program that creates 100 threads that does nothing but wait, and see how much memory the application takes when running.



