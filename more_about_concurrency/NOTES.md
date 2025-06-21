# Go Programming: More about Concurrency

## Concurrency vs Parallelism

- Concurrency: The ability of a system to handle multple tasks simultaneously. It involves managing multiple tasks that are in progress at the same time but not necessariliy executed at the same instant.

- Parallelism: The simultaneous execution of multiple tasks, typically using multiple processors or cores, to improve performance by running operations at the same time.

- Parallelism is all about executing multiple  tasks simultaneously, typically on multiple cores or processors and this is a subset of concurrency. 

    How parallelism is implemented in GO ?
    - It's the go runtime. Go's runtimes scheduler can execute Go routines in parallel, taking advantage of multiple core processors.

    <img src="./assets/concurrency_vs_paralleism_2.png" width="650" alt="Concurrency vs Parallelism"/>

- We can have processes that are executed concurrently without being parallel. And that happens when we have a single core CPU with time slicing. The single core CPU will divide time using time slicing and work on those multiple tasks simultaneously by dividing time and giving time to different functions, different tasks in a shared way. eg: So maybe 200 milliseconds to a tasks and then next 200 ms to another tasks and next 50 ms to the first task that it left earlier, and so on.

- Practical Applications:
    - Concurrency Use cases:
        - I/O bound tasks
        - Server Applications
    - Parallelism Use Cases
        - CPU Bound tasks
        - Scientific Computing

- Challenges and Considerations :
    - Concurrency Challenges
        - Synchronization: managing shared resources to prevent race conditions.
        - Deadlocks: avoid situations where tasks are stuck waiting for each other.
    - Parallelism Challenges
        - Data Sharing
        - Overhead
    - Performance Tuning




## Race Conditions

- A race condition occurs when the outcome of a program depends on the relative timing of uncontrollable events such as thread or goroutine scheduling. It usually happens when multiple threads or goroutines access shared resources concurrently without proper synchronizatino, leading to unpredictable and incorrect behavior.

- Why does it matter ?
    - Race conditions can cause bugs that are difficult to reproduce and debug, leading to unreliable and inconsistent program behavior.

- To check if the program has a race condition, add the `-race` flag during running the program.
    ```go
    go run -race race_conditions.go
    ```
    - When we have multiple goroutines accessing the same value, trying to modify the same value or trying to do something at the same time with a same type/variable/object, then in that case, use this `-race` flag and find if you have a data race in your program.

- Go provides a builtin race detector tool that helps identify the race conditions in your programs. The race detector monitors accesses to shared variables and reports data races during execution. Finally in the output, the race detector shows where data races occur including the read and write operations.

- We use mutexes or stateful goroutines or atomic operations to avoid race conditions.

- Best Practices to Avoid Race Conditions :
    - Proper Synchronization: use synchronization primitives like mutexes or atomic operations to ensure exclusive access to shared resources.

    - Minimize Shared State: reduce the amount of shared state between concurrent operations to lower the risk of race conditions.

    - Encapsulate State: use encapsulation to manage state within structs or functions limiting exposure to shared data.

    - Code Reviews and Testing: regularly review code for potential race conditions and utilize tools like the race detector to identify issues during development.

- Practical Considerations
    - Complexity of Synchronization
    - Avoiding Deadlocks
    - Performance Impact



## Deadlocks





## RWMutex





## `sync.Once`






## `sync.Pool`





## `for select` statement





## Advanced Concurrency Quiz