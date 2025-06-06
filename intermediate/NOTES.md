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

- Go offers many formatting verbs to be used with `printf` statement.

- **General Formatting verbs**:
    - %v  -> Prints the value in the default format
    - %#v -> Prints the  value in Go-syntax format
    - %T  -> Prints the type of the value
    - %%  -> Prints the % sign

- **Integer Formatting Verbs**:
    - %b    -> Base 2
    - %d    -> base 10
    - %+d   -> Base 10 and always show sign
    - %o    -> Base 8
    - %O    -> Base 8 with leading 0o
    - %x    -> Base 16, lowercase
    - %X    -> Base 16, uppercase
    - %#x   -> Base 16 with leading 0x
    - %4d   -> Pad with spaces (width 4, right justified)
    - %-4d  -> Pad with spaces (width 4, left justified)
    - %04d  -> Pad with zeroes (Pads an integer with zeroes to ensure it has minimum width of 4 digits)

- **String Formatting Verbs**:
    - %s    -> Prints the value as plain string
    - %q    -> Prints the value as a double-quoted string
    - %8s   -> Prints the value as a plain string (width 8, right justified)
    - %-8s  -> Prints the value as a plain string (width 8, left justified)
    - %x    -> Prints the value as hex dump of byte values
    - % x   -> Prints the value as hex dump of byte values with spaces

- **Boolean Formatting Verbs**:
    - %t    -> Value of the boolean operator in true or false format (same as using %v)


- **Float Formatting Verbs**:
    - %e    -> Scientific notation with 'e' as experiment
    - %f    -> Decimal point, no exponent
    - %.2f  -> Default width, precision 2
    - %6.2f -> Width 6, precision 2
    - %g    -> Exponent as needed, only necessary digits


- Go syntax format refers to format in which values are represented in Go code. For example, strings are enclosed in double quotes.




## `fmt` Package

- The `fmt` package includes functions for printing to standard output, returning formatted strings and snaning input.

- Some Key Functions of fmt package : 
    - Printing functions
        - Print()
        - Println()
        - Printf()
    - Formatting Functions
        - Sprint()
        - Sprintf()
        - Sprintln()
    - Scanning Functions
        - Scan()
        - Scanf()
        - Scanln()
    - Error Formatting functions
        - Error()

- We hace the `Sprint()` function which formats using the default formats for it's operands and returns the resulting string. It doesn't print anything to the console. It only returns the resulting string.

- The formatting functions that we have in Go like Sprint(), Sprintln(), etc., these quite evidently can also be used to concatenate strings. 

- Sprint() does not add a space in between the different values.

- Sprintln() is a little advanced method which adds spaces in between the arguments and also adds a new line character at the end.

- Sprintf() function formates according to a format specifier and results the resulting string.

- fmt pacakge also brings us some functions that can help us take input from the user through the console.

- The `Scan()` function scans the text from the standard input and stores it into the provided variables. So we have to provide a variable for the input to be stored into.

- We have to the direct memory address to scan the input and store it inside the variables passed in the scan function. Because if we pass variables as arguments, the actual variable will not be passes to the function, instead a copy of that variable will be passed, so all the modifications will be done on the copy of the variable and not the actual variable. In order for us to modify the actual variables we give the memory address to `fmt.Scan()`.

- Moreover, Scan() has three dots that means it can accept `Variadic Parameters`. That means it can be multiple parameters or none.

- `Scanln()` function is similar to Scan() but it stops scanning at a new line and requires that there be exactly one item per input.

- Scan() does not accepts a blank input

- `Scanf()` function scans text from standard input, storing successive space separated values into successive arguments as determined by the format specifier.

- We have to enter our inputs in the exact format that we have declared in the `Scanf()` function.

- The `Errorf()` function formats according to a format specifier and returns the string as a value that satisfies the error interface.

- If there's an error, first we declare a code block to handle the error and then we move on to handling the value, whatever we want to do with the value.

- In conclusion, the fmt package is an essential tool for Go developers providing robust functions for formatting and printing text, scanning input and handling errors.

- In APIs `Sprint()` functions are used extensively.



## Structs

- Structs in Go are composite data types that allow you to group together different types of variables under a single name. They are similar to classes in Object Oriented Languages, but they are more lightweight and do not support inheritance.

- Structs are defined using the `type` and `struct` keywords followed by curly braces `{}` containing a list of fields. 
- Fields are defined with a name and a type.
- Anonymous Structs
- Anonymous Fields

- Methods : 
    ```go
    func (value/pointer receiver) methodName(arguments, if any ...) <return type, if any> {
        // Method implementation
    }
    ```

- Method Declaration
    - Value receiver method
        ```go
        func (t Type) methodName() {
            // Method Implementation
        }
        ```
    - Pointer receiver method
        ```go
        func (t *Type) methodName(){
            // Method Implementation
        }
        ```

- Comparing Structs

- Structs can be initialized using a struct literal. We can provide values for individual filed during initialization. As with any variable, if we omit any field in a struct, it will be initialized with it's zero value.

- Fields are accessed using a dot notation.

- Similar to functions we also have anonymous structs. These anonymous structs are structs without a predefined type name. They are useful for temporary data structures.

- Go supports attaching methods to structs. Methods are functions associated with a specific type. Methods are defined with a receiver, which is the struct type upon which the method operates.

- Always define methods and structs outside the main function. Defining alone a struct inside main is fine but when there are methods associated with that struct inside the program, we cannot define the methods inside main function. 

- Structs and methods must be defined at the package level, not within the functions. It is by design in Go and that is because Go requires types and their associated methods to be declared in the global scope which is accessible throughout the package.

- Another reason why structs and methods cannot be inside main is because of separation of concerns. Keeping type definitions and methods outside the main function ensures clear separation between data definitions and execution logic. This makes code more readable and more maintainable.

- We can create instances of structs and we can call methods on those instances inside the main function. And other thing that we can do inside main function is implement our application logic and interact with our structs and their methods.

- We do not configure the methods inside the structs. So why are methods not inside struct declarations ?
    - the first reason is design philosophy. Go emphasizes simplicity and clear separation between data types and methods. Methods are defined outside of the struct declaration to maintain a clear distinction between data and behaviour. The behaviour is dependent on the methods and data is the data types, the properties of the classes and the structs.

    - However in classes, we have class properties and methods inside the same class. The class properties of classes are like data types and the methods are similar to the methods declared in Go langauge.

    - Another reason is flexibility. Now this approach that we are defining the methods separately from structs, this approach allows methods to be defined for any type, not just structs and facilitates code organization and modularity.

- To modify struct fields within a method, we use a pointer receiver instead of a value receiver. Pointer receivers allow the method to modify the original struct instance.

- Pointers make the actual memory address available to the function. But if we are using value receiver it means we are passing the value to a function and it will not modify the original value. So in order to access the original value and modify that, we have to use a pointer.

- Go supports embedding structs within other structs. This allows for creating a composition of structs.

- We can define structs with anonymous fields as well. It simplifies the structure definition by promoting the fields of the anonymous struct to the outer struct. In Go, anonymous fieds in struct must be a type. If you declare a field like phone it needs to be of a specific type.

- Anonymous fields simplify the structure definition by promoting the fields of the anonymous struct to the outer struct.

- Structs are comparable if all their fields are comparable. You can compare two structs of the same type using the equality operator.



## Methods

- We make methods by declaring a receiver. The receiver will be a struct and that receiver will be associated with that method. So these methods are functions associated with a particular type not necessarily with struct. 

- So methods are not just associated with structs. They can be associated with any specific type. Methods enable us to define behaviors and we define behaviours by using functions. So we define these behaviors that operate on instances of that type.

- Methods are essential in Go for encapsulating behavior specific to a type and promoting code reuse through structured and organized code. 

- Methods are declared with a receiver which specifies the type that the method operates on and there are two type of receivers in Go : value receivers and pointer receivers.

- We use a value receiver if the method does not modify the receiver instance. We use a pointer receiver if the methos needs to modify the receiver instance, or if you want to avoid copying large structs because copying large structs means you are occupying a bing chunk in the memory.

- It's not a thumb rule that you have to create an instance. You can use the type to associate the function with that type to make it a method of that type.
    ```go
    type MyType int

    func (MyType) welcomeMessage() string{
        return "Welcome to MyType"
    }
    ```
    - We don't need an instance because we are not accessing any data inside this type. So we need to use instance only if we are using the instance for extracting or modifying the value.

- Struct embedding allows methods of an embedded structs to be promoted to the outer struct.


## Interfaces

- Interfaces promote code reuse, decoupling and polymorphism without relying on explicit inheritance.

- An interface is declared using the `type` keyword followed by a name and keyword `interface` and a list of method signatures.

- Interfaces are also declared outside the main function.

- A type implicitly satisfies an interface if it implements all the methods defined by that interface.

- Any method or any function that needs to be exported should start with an uppercase letter. So in order for us to export any method, struct or any type we have to name that type with an uppercase alphabet.

- All a struct needs to do is implement all the methods defined in that interface. All the methods that are defined in an interface should be implemented by that struct to be able to get associated with that interface type.

- An interface in Go is a way to define a set of methods that other types must implement in order for them to be considered the type that, which the interface if of.

- `any` is an alias of interfaces.

- We can use interface when we are ready to accept any type of value in our function. So if I use a vairadic parameter that means we can accept any number of values of different types.

- Interface means that you are flexible to any kind of value.

- Use empty interfaces judiciously typically for scenarios requiring dynamic types or unknown types.

- Interfaces in Go facilitate Polymorphism and enable writing modular, testable and maintainable by promoting loose coupling between types.


## Struct Embedding

- Struct embedding allows a struct to inherit fields and methods from another struct type. It's a powerful mechanism for code re-use and structuring data.

- Methods can be overridden by redefining them in the outer struct.

- Anonymous fields promote all fields and methods of the embedded struct while named fields require accessing fields with their explicit names.

- Best Practices and Considerations
    - Composition over inheritance
    - Avoid Diamonf Problem
    - Clarity and Readability
    - Initialization



## Generics

- Generics in programming languages provide a way to write functions, data structures and algorithm that can handle various types without specifying each type explicitly. This promotes code re-use, type safety and enhances the flexibility of programs.

- Generics in go are declared using type parameters, which are placeholders for types that can be specified when using the generic function or data structure.

- `any` is just an alias for interface and interface means that it can be of any type.

- Benefits of Generics :
    - Code Reusability
    - Type Safety
    - Performance

- Considerations
    - Type Constraints
    - Documentation
    - Testing



## Intermediate Quiz 1

![Quiz 1](./assets/quiz1/q1.png)
<br/>

![Quiz 1](./assets/quiz1/q2.png)
<br/>

![Quiz 1](./assets/quiz1/q3.png)
<br/>

![Quiz 1](./assets/quiz1/q4.png)
<br/>

![Quiz 1](./assets/quiz1/q5.png)
<br/>


## Errors

- Errors are a funcdamental part of any programming language, allowing programs to handle exceptional conditions gracefully.

- In Go, Errors are represented by the error interface, which is a built-in type used to indicate the presence of an error condition. 

- Errors are typically created by using the `errors` package or by implementing the error interface.

- Do not unnecessarily use uppercase when naming structs or any other type, always make sure that you use uppercase only when you are exporting your type, your struct or anything else outside the package.

- Example:
    ```go
    func main() {
        if err1 := eprocess(); err1 != nil {
		fmt.Println(err1)
		return
	    }
    }
    type myError struct{
	message string
    }

    func (m *myError) Error() string{
        return fmt.Sprintf("Error: %s", m.message)
    }

    func eprocess() error {
        return &myError{"Custom Error Message"}
    }
    ```
- We are using Error() because Go has a built-in package. The Go's built in package have an interface which is the error interface. The error interface has a single method which is `Error()`. An in Go an error is represented by the error interface, and this error method returns a string that describes the error.

- So by utilizing this interface, we can propagate our custom error messages as we please. Because it is an interface, we can modify it according to our requirements. We can use multiple lines, multiple kinds of data. We can use different kinds of formatting whatever we want because it is an interface. And interfaces are completely blank, all you need to do is implement the methode.

- Official error interface implementation of Go
    - [Offical Go Builtin Package github](https://github.com/golang/go/blob/master/src/builtin/builtin.go)

    ![Error Interface](./assets/error_interface.png)

- Error method needs to return a string and that's why our Error() method returned a string. 

- When we are using any function from the built in package it is available to us by default. The built-in pacakage is part of the Go runtime and is special in that it provides the foundations for the language itself. Therefore you can use fundamental types and functions directly in your code.

- In conclusion, error handling in go revolves around the error interface and idiomatic practices like checking errors, propagating errors and custom error types. Proper error handling ensures that programs are robust and reliable, providing clear feedback on exceptional conditions.



## Custom Errors

- Custom Errors can encapsulate specific details about what went wrong, making it easier to debug and understand the root cause of errors. It provides an enhanced error context.

- Context and custom errors allow us to distinguish between different types of errors and handle them differently in our application logic.

- Custom errors also ensures consistency in error handling accross our code base, promoting maintainability.

- In Go, custom errors are nothing but types that implement the error interface. It requires the implementation of errxor method that returns a string.

- When we are handling errors, we have to return so that the rest of the statements do not get executed. That's the point of handling the error, right ?

- **Wrapped Errors** : Wrapped Errors were introduced after Go version 1.13. `%w` formatting verb stands for wrapped error.

- Our custom error helps us to pass on the error message much more efficiently and much better error description from multiple functions that we are executing in a nested way.

- In conclusion, custom errors in go enhance our error handling by providing more context and differentiation in error reporting.


## String Functions

- Strings in go are a sequence of bytes and Go provides a rich set of built-in functions and methods to manipulate and work with strings effectively.

- Functions
    - integer to string : 
        ```go
        num := 18
        str := strconv.Itoa(num)
        ```

    - string splitting
        ```go
        fruits := "apple,orange,banana"
        parts = strings.Split(fruits, ",") // ["apple", "orange", "banana"]
        ```
        - `strings.Split()` converts your original string into an array and it divides that string based on the seperator value that you give it.

    - `strings.Join()` -> concatenates elements of a slice into a single string with a separator.
        ```go
        countries := []string{"Germany", "France", "Italy"}
        joined := strings.Join(countries, ", ")
        ```

        Go is smart enough to add separator only between the consecutive words and not after the last word.

    - Function to check if a string contains a subset characters, it could be one character or multiple characters combined.
        ```go
        strings.Contains(str, "test") // returns true or false.
        ```

    - `strings.Replace()` -> Replaces the occurances of a substring within a string with another substring.
        ```go
        strings.Replace(str, <string to be replaced>, <string by which it is replaced>, <no. of occurances to be replaced>)

        strings.Replace(str, "Go", "World")
        ```

    - We can also trim leading and trailing whitespace from our string. 
        ```go
        strwspace := " Hello Everyone! "
        fmt.Println(strwspace.TrimSpace(strwspace)) // "Hello Everyone!"

    - We can change the case of our strings to lower or to upper during the runtime.
        ```go
        fmt.Println(strings.ToLower(strwspace))
        fmt.Println(strings.ToUpper(strwspace))
        ```

    - `strings.Repeat()` -> repeat something for a fixed number of times.
        ```go
        fmt.Println(strings.Repeat("foo", 3))  // foofoofoo
        ```
    - We can also count the occurance of an alphabet or a substring inside another string.
        ```go
        strings.Count("Hello", "l")   // 2
        ```

    - We can also check for prefix and suffix. 
        ```go
        fmt.Println(strings.HasPrefix("Hello", "He")) // true
        ```

        ```go
        fmt.Println(strings.HasSuffix("Hello", "la")) // false
        ```
 
- Go offers us a regular expression package which allows pattern matching and manipulation of strings based on complex rules.

- `regexp` is a package in Go and `MustCompile()` is a method defined in `regexp` package.

- MustCompile() -> is a function that compiles a regular expression. A regular expression is something yes which needs to be compiled. 

- The pattern needs to be inside Backticks. Regular Expressions needs to be enclosed in backticks to be considered a raw string literals. When we are using regular expressions we are defining a pattern and that pattern needs to be matched. So regular expression matches the pattern that we define with different values.

-  d -> digits
    +   -> it has to be one or more
    eg: `\d+`   -> It has to be one or more digits
                -> check for multiple digits
    
    ```go
    str5 := "Hello, 123 Go! 78"
    re := regexp.MustCompile(`\d+`)
    matches := re.FindAllString(str5, -1)
    fmt.Println(matches)
    ```

    -1 indicates that we are looking for all the matches for that regular expression inside the source string.

    `FindAllStrings()` -> returns an array of strings. It's going to extract all the matches and store them successively in a slice. So it returns a slice of strings. So we have to store the slice in a variable.

- We have another package which let's us work on Unicode characters and strings and that is called the unicode `utf8` package. `utf8.RuneCountInString` returns the number of runes present in the string.

- Since strings are immutable in Go, we have something called `strings.Builder()` for efficient string concatenation in performance critical scenarios.

- `strings.Builder()` is a type in Go's standard library specifically in the strings package that provides efficient strings building. It's designed to help you concatenate strings in a memory efficient wat instead of creating many intermediate strings, which can be expensive in terms of memory and processing time. `strings.Builder()` allows you to build your final string incrementally.

- strings.Builder() is more efficient than using the concatenation (`+`) operator or even when using `fmt.Sprintf()` fo concatenating multiple strings. strings.Builder is still much better than these options because it minimizes memory allocations and copies.

- Builder provides several ways for adding content such as write, writeString, writeRune and writeByte. and builder can be used immediately after declaration without initialization.

- A builder can be reused by calling the reset method which clears it's internal buffer. The final string can be retrieved using the string method.

- We can keep on building that string. And this builder is memory efficient and prevents memory leaks. It does not make copies. It keeps on building the string in a memory efficient way and in a memory secure way.

- we have to include character in `builder.WriteRune()` and characters are stored in single quotes.

- builder keeps on writing to the existing string that it has stored in its memory. So everything that we write a rune, a string or anything, it will keep on adding to the existing data that it has.

- So in order for us to start a new string, we need to reset the builder.

- When it comes to memory efficiency, prefer strings.Builder or bytes.Buffer for building large strings to avoid unnecessary memory allocations.



## String Formatting

- String formatting in Go refers to the techniques used to create formatted output from variables or constants. Go provides several mechanisms for formatting strings, including the fmt package, string interpolation or format specifiers.

- When it comes to format specifiers, we can use flags or string alignment as well to format our strings in a desired way.

- Go supports string interpolation using backticks.
- BAckticks makes a string raw, a raw string literal, which means that it is going to consider everything as a string literal and it's not going to let any escape sequence execute.

- When you need to embed special characters or multiple lines of text without interpreting escape sequences, backticks are very useful. This is particularly handy when dealing with regular expressions. This improves readability and reduces the chances of errors due to missed escape sequences.

- Another use case would be when we are using SQL query. So in SQL queries using backticks ensures that the query remains intact without needing to escape special characters or worry about line breaks. It enhances readability and reduces the cognitive load when writing or maintaining such code.




## Text Templates

- Text templates in go are a powerful feature that allow you to define and execute templates for generating text output. They are particulary used when you need to generated structured texts wuch as HTML, JSON, SQL Queries or any other formatted text output.

- A template is a string or a file that contains one or more action sequences. These actions control the template execution, such as inserting values, iterating over data or executing conditionals.

- Concept of Actions: These actions are enclosed in double curly braces. There are several types of actions like variable insertion.

    - Variable Insertion: [{.FieldName}]
    - Pipelines: {{functionName .FieldName}}
    - Control Structures: {{if .Condition}} ... {{else}} ... {{end}}
    - Iteration: {{range .Slice}} ... {{end}}

- Advanced Features
    - Nested Templates: {{template "name" .}}
    - Functions
    - Custom Delimiters
    - Error Handling: template.Must()

- Use Cases
    - HTML Generation
    - Email Templates
    - Code Generation
    - Document Generation

- Best Practices
    - Separation of Concerns
    - Efficiency
    - Security

- Templates are executed by applying them to data structures known as Template Data. These data structures can be simple values, structs, slices, maps or any custom types that you define.

- Templates are a part of 2 packages:
    - We have text template as well as html template package. HTML template package has some advanced features that text template package does not have. Text template package has basic features of templating. 

- Once we have create a template, we have to parse the template, we have to process that template. We use `.Parse()` method. It takes an argument which is a string, but this string is not a usual string. This is actually a string that we want to be processed as a template.

- Template is something that we can reuse repeatedly for different values, and the name is going to be changing everytime we use this template. 

- To output the message from the template use `.Execute()` function on that template. It will return an error if there is one so make sure to handle the error in a variable.
    ```go
    err := tmpl.Execute(os.Stdout, data)
    ```

- Execute takes the first argument as the target, the destination where it needs to send the output to. So we are sending our output to the standard output device of our computer which is the console. And the next argument is the data.

- There's another way of using template via using `template.Must()` where we don't have to handle the errors ourselves and template.Must() will automatically panic if we have an error while parsing our template.

    ```go
    tmpl := template.Must(template.New("example").Parse("Welcome, {{.name}}! How are you doing?\n"))
    ```

    this code is equivalent to :
    ```go
    tmpl, err := template.New("example").Parse("Welcome, {{.name}}! How are you doing?\n")
    if err != nil {
        panic(err)
    }
    ```
- .Must() is used to handle the error from the parse. And we'll not have to handle the error ourselves, which will save us some more typing and which will make our code mmore readable.

- template.New() -> creates a new template and it takes the name of the template as an argument.

- template.Parse() -> parses the template definition. So it takes a string and that string is in the format of template that we want. And then template.Parse will process the string and convert it into a template that we will use further in our program. So `template.Parse()` helps us to parse the template string and it turns the string into a reusable template object that can be executed with custom data.

- `template.Execute()` -> used to apply a parsed template to a data structure and write the result to an output destination. It could be a file or it could be a console or something else.

- `bufio` -> Buffered input output package.
- `bufio.NewReader(os.Stdin)` -> to read from the console. Console is the standard input device.
- to get the input from the user :
    ```go
    reader := bufio.NewReader(os.Stdin)
    ```

- .ReadString() -> takes an argument as a delimeter. So that means it is going to accept the input from the console until it reads the delimeter from the console. It takes a `bytes` type as an argument, that's why we have to use single quotes.
    ```go
    reader.ReadString('\n')
    ```
- `ReadString()` -> generates a string and an error so handle both of them by storing them in the variable. Always read strings from the console and then convert them to whatever you want.

- Best Practices
    - Separation Of Concerns: Keep your templates focused on presentation logic avoiding business logic.
    - Precompile you templates for re-use if performance is critical to your application.
    - Also sanitize inputs to prevent injection attacks, especially when generating HTML because there are a lot of attacks which happen using the user input.

- Overall, text templates in Go are a powerful tool for generating textual output based on structured templates and dynamic data. They offer flexibility, ease of use and support for complex scenarios like conditional logic, iteration and function invocation within templates whether for web applications, system administration scrips or data processing tasks.



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