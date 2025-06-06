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

- A string is a sequence of bytes. Bytes are unsigned int8 (`uint8`) values. They often represent text. A sequence of bytes represent text.

- Strings are immutable meaning, once created, their values cannot be changed.

- Strings can be created with double quotes `" "` or backticks "`". Backticks are used for raw string literals. In raw string literals the escape sequences will be discarded and everything will be treated like a character and it will print everthing out the way it was written.

    ```go
    message := "Hello\nWorld"  // Hello and World on different line
    rawMessage := `Hello\nWorld`  // Hello\nWorld as output

    message2 := "Hello, \rGo!"  // Go!lo,
    ```
- `\r` takes the cursor to the first position in the line.

- Strings are an array of unicode characters. And these unicode characters i.e. each alphabet that we see, in Go it is called `rune`.

- Rune is an integer value that represents a character.
- Since strings is an array of characters, it also has a length. We can get the length of the string using the same `len()` function for arrays, slices.

- All escape sequences are treated as 1 character.

- When we are using concatenation, we are joining two strings. And when Go is joining two strings, it will not autmatically insert a space between them. It only happens when we are using a print statement and we are using thode different variables seperated by a commas. So it knows, that these are different variables with different content and they could mean different, so that's why it automatically inserts a space between them. But when it comes to concatenation, it knows that we want to join two strings and that's why it doesn't apply any space in between.

- Lexicographic Comparison : It is a method of comparing sequences such as strings based on the alphabetical order of their components. In Go, lexicographic comparison is used to compare strings. This comparison is essential for sorting, searching and other operations that involve ordering strings.

- If one string is a prefix of another, the shorter string is considered smaller.

- The compiler is comparing the ASCII value of the characters.

- When it comes to string iteration, it's just like iterating over a slice or an array. It will have an index and a value.

- `%x` placeholder/format verb is used to get the hexadecimal value of a character.

- `RuneCountInString()` -> counts the utf-8 characters in a string.

- Strings a immutable that means, operations like appending, replacing or modifying, require creating new strings. So we have to manipulate strings by creating new strings.

- We cannot append append more runes, more characters at the end or in the middle or in the begining using any method. So for that we have to create a new string and then perform a concatenation or whatever that we want to manipulate those string variables.

- A `rune` is an alias for int32 and it represents a Unicode code point, a Unicode value. So it is not a character, it is an integer value. A rune is an integer value and that value represents a Unicode code point and that will be converted into a character.

- So runes are used to represent individual characters in a string, and they facilitate working with Unicode characters efficiently. 

- Using Unicde, Go encopassess characters from a lot of languages accross the globe and that makes the jobs of the programmers much easier because we have characters from many, many languages that are used accross the world.

- A rune is declared with the type as `rune`. Runes are declared using single quotes. Double quotes and backticks are for strings.
    ```go
    var ch rune = 'a'
    ```

- Rune literals are single quoted characters representing Unicde code points.

- Runes facilitate handling of Unicode characters, supporting internationalization and mutilingual text processing.

- We have support for Smileys in Go language. We can use smileys directly in go as chacters.

- Strings provide a convenient abstraction for working with textual data, while runes enable precise handling of individual characters and support for diverse languages.

- Runes and Characters
    - Similarities
        - Representing Characters
        - Storage Size
    - Differences
        - Unicode Support
        - Type and Size
        - Encoding and Handling

- Both runes and characters typically occupy a fixed amount of memory. Runes in Go are represented by int32 and represent 4 bytes of memory, allowing them to represent any unicode code point characters. But characters are usually represented by `char` which typically occupy one byte of memory.

- Runes can represent any unicode code points from ASCII to more complex characters like emojis and non-latin scripts as well. While C also supports characters beyond ASCII through multibyte encodings like utf-8, handling unicode characters directly is not as straightforward as in Go. C libraries and implementations may vary in their support for Unicode.

- Go natively supports Unicode and provides built-in support for handling runes through it's `rune` type and unicode utf-8 package as well. This makes it straight forward to iterate over and manipulate Unicode strings.

- So Go's native support for Unicode and runes make it easier to develop applications that need to handle diverse character sets and languages. So if we are making an appplication where we need to generate text in different languages. Go has a native support for all the languages world-wide.

- Runes provide a more modern and robust approach for handling Unicode and international text representing Go's design philosophy of simplicity and efficiency in text processing.



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