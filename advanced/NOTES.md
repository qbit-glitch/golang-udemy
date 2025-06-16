# Go Programming Advanced

## Goroutines

- Goroutines are lightweight threads managed by the Go runtime. They enable concurrent execution of functions, allowing you to perform multiple tasks concurrently within a single Go program.

- Goroutines are one of the key features of GO making it easy to write concurrent and parallel programs. We use Go routines to efficiently handle parallel tasks such as input output operations, calculations and more.

- Goroutines provide us a way to perform taks concurrently without manually managing threads. To create a new goroutine, we use `go` keyword preceding the function and execute that function immediately in the main function.

- Why use Goroutine:
    - Simplify concurrent Programming
    - Efficiently handle parallel tasks such as i/o operations, calculations and more.
    - Provide a way to perform tasks concurrently without manually managing the threads.

- Basics of Goroutines:
    - Creating Goroutines (use the `go` keyword to start a new Goroutine)
    - Goroutine Lifecycle
    - Goroutine Scheduling

- Goroutines are just functions that leave the main thread and run in the background and come background and come back to join the main thread once the functions are finished/ready to return any value.

- Goroutines do not stop the program flow and are non-blocking in nature. Similary to async await and promises in Javascript. Goruntime handles the goroutines. It immediately extracts the function preceding with `go` keyword out of the main thread.

- Goroutine Life cycle: 
    - A goroutine starts when created and runs concurrently with other goroutines. 
    - A goroutine exits when the function it is running completes. So goroutine contains a function and if the function completes, then it exits.

    - It's the GoRuntime that manages goroutine scheduling and execution.

- What is Goroutine Scheduling ?
    - Goroutine scheduling is managed by the Goruntime scheduler. It uses M:N scheduling model. M goroutines run on N os threads.
    - Another thing that the goroutine scheduling does is that it efficiently multiplexex goroutines onto available threads.

- Go uses M:N scheduling model where, M goroutines are mapped onto N operating system threads. Your processor have cores and threads and your goroutines are mapped onto those limited number of cores and threads. This model allows goruntime to manage many Go routines with fewer operating system threads, improving efficiency and scalability. The goroutine scheduler efficiently multiplexex Go routine onto available threads.

- Multiplexing is like switching. Goroutine scheduler multiplexes or switches goroutines onto available OS threads. The scheduler is switching goroutines onto the available operating system threads. It means, it can run many goroutines on a limited number of threads by dynamically scheduling and rescheduling goroutines as needed. And this efficient use of resources ensures high concurrency and performance.

- Goroutine Scheduling in Go :
    - Managed by the Go runtime scheduler
    - Uses M:N scheduling model
    - Efficient Multiplexing

- Common pitfalls and best practices
    - Avoiding Goroutine leaks
    - Limiting Goroutine creation
    - Proper error handling
    - Synchronization


- Goroutine execution is concurrent in nature. And Goroutines run independently and concurrently.

- Concurrency vs Parallelism overview :
    
    - Concurrency means multiple tasks progress simultaneously and not necessarily at the same time. But parallelism states that tasks are executed literally at the same time on multiple processors. So goroutines facilitate concurrency and the goruntime scehdules them accross available CPUs for parallelism when possible.

    - So goroutines are a tools that Go has provided us to make use of concurrency in Go programs and Goruntime schedules thos go routines accross the available CPU threads, CPU cores for parallelism if it is possible.

- Associated topics:
    - Wait groups
    - Worker pools
    - Channels

- Handling Errors in Goroutine through a concept called error propagation. So goroutines execute functions concurrently and in that case errors need to be communicated back to the main thread, so use return values or shared error variables if not using channels. So if we are not using channels we can use shared error variable.






## Channels - Introductions




## Unbuffered Channels and Runtime Mechanism



## Buffered Channels




## Channel Synchronization





## Advanced: Quiz-1





## Channel Directions




## Multiplexing using Select




## Non-Blocking channel operations





## Closing Channels





## Advanced: Quiz-2





## Context





## TImers





## Tickers






## Worker Pools





## Wait Groups





## Advanced: Quiz-3





## Mutexex






## Atomic Counters






## Rate Limiting






## Rate Limiting - Token Bucket Algorithms





## Rate Limiting - Fixed Window Counter






## Rate Limiting - Leaky Bucket Algorithm






## Stateful Goroutines





## Sorting





## Advanced: Quiz-4





## Testing / Benchmarking






## Executing Processes / OS Processes / Other Processes





## Signals





## Reflect






## Advanced: Quiz-6






