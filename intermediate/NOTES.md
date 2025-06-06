# Go Programming: Intermediate

## Closures

- A closure is a function value that references variables from outside it's body. The function may access and assign to the captured variables, and these variables persist as long as closure itself is referenced.

- Closures work with lexical scoping, meaning they capture variables from their surrounding context where they are defined. This allows closure to access variables even after the outer function has finished execution.

- Closures leverage the first class objects property of functions by allowing functions to capture and manipulate their surrounding state.

- Code Summary : 
    - i and the gofer assignment zero line and the fmt.Println("Previous values of i:") run everytime you call the adder function, but they only affect the initial state of i. When you create a new closure by calling sequence but they only affect the initial state of i when you create a new closure by calling adder function.

    - Once the closure is created, the subsequent calls to the closure that is, the returned function use and modify the captured value of i.

- Practical Use Cases
    - Stateful functions
    - Encapsulation
    - Callbacks

- Usefulness of Closures
    - Encapsulation
    - Flexibility
    - Readability

- Considerations
    - Memory Usage
    - Concurrency

- Best Practices
    - Limit Scope
    - Avoid Overuse

- Closures are useful for creating functions that maintain state accross multiple calls without exposing the state directly.

- They help encapsulate functionality and data, allowing for cleaner and more modular code.

- Closures are commonly used in callback functions, where they capture cariables to provide context or maintain state during asynchronous operations.

- Closures can keep variables alive longer than expected if they hold references to large objects or resources.

- Care must be taken when using closures in concurrent programs to avoid race conditions and unintended side effects. That's why it's better to limit the scope. Keep the scope of captured variables enclosures as narrow as possible to minimize unintended side effects.

![Closures in Go](./assets/closures.png)


## Recursion

- Recursion is the process of a function calling itself. It breaks down a problem into smaller sub-problems of the same type until they become simple enough to solve directly.

- In every recursive function, there is a base case which is a condition where the function stops calling itself and returns a value. Without a base case, the recursion would continue indefinitely, leading to a stack overflow. And apart from the base case we have a recursive case. This is where the function calls itself with a smaller or simpler input to make progress towards the base case.

- Practical Use cases : 
    - Mathematical Algorithms
    - Tree and Graph Traversal
    - Divide and Conquer Algorithms

- Benefits of Recursion
    - Simplicity
    - Clarity
    - Flexibility

- Considerations
    - Performance
    - Base Case

- Best Practices
    - Testing 
    - Optimization
    - Recursive Case

- Sometimes a recursive solution can be optimized using techniques like memoization. Memoization is caching results of expensive function calls.


## Pointers

- A pointer is a variable that stores the memory address of another variable. 

- Everytime we execute go run, a new executable is made. So Go Run makes a temporary executable each time we execute `go run`.

- The zero value of a pointer is `nil`

- When we are using pointers, the actual memory address of the variable is passed on to the function. And now the function is accessing the memory address where the number ten is stored by a.

- Use cases : 
    - Modify the value of a variable indirectly
    - Pass large data structures efficiently between functions
    - Manage memory directly for performance reasons.
- Pointer Declaration and Intialization
    - Declaration Syntax :
        ```go
        var ptr *int
        ```
        `ptr` is a pointer to an integer
    
    - Initialization :
        ```go
        var a int = 10
        ptr = &a
        ```
        `ptr` now points to a's memory address

- Pointer Operations: Limited to referencing(`&`) and dereferencing(`*`)

- Nil Pointers
- Go does not support pointer arithmetic like C or C++
- Passing Pointers to functions
- Pointers to Structs
- Use pointers when a function needs to modify an argument's value
- `unsafe.Pointer(&x)` converts the address of `x` to `unsafe.Pointer`

- We will be taking up gRPC and Protocol Buffers and we will be using pointer a lot in Protocol Buffers and gRPC.

- Go also have an `unsafe` package and go's unsafe package allows low level operations like direct memory access and typecasting useful in certain advanced scenarios.

- In conclusion, understanding and mastering pointers in Go opens doors to more efficient memory management, enhanced control over data structures and access to low level operations when necessary.


## String and Runes



## Formatting Verbs



## `fmt` Package



## Structs



## Methods



## Interfaces



## Struct Embedding



## Generics



## Intermediate Quiz 1



## Errors



## Custom Errors



## String Functions



## String Formatting




## Text Templates




## Regular Expressions



## Time



## Epoch



## Time Formatting / Parsing




## Random Numbers



## Number Parsing



## Intermediate Quiz 2



## URL Parsing



## `bufio` package



## Base64 Coding



## SHA256 / 512 Hashes / Hashing / Cryptography




## Writing Files



## Reading Files



## Line Filters



## File Paths



## Directories




## Temporary Files and Directories




## Embed Directive




## Intermediate Quiz 3




## Command Line Arguments / Flags



## Command Line Sub Commands



## Environment Variables



## Logging



## JSON




## Struct Tags



## XML



## Go Extension



## Type Conversions



## IO Package




## Math Package




## Intermediate Quiz 4