## Import

- Tree Shaking and it's application
    - Tree shaking
    - Static Analysis
    - Dead Code Elimination

- Example in Popular Frameworks
    - React
    - Angular

- Benefits of Tree Shaking
    - Reduced Bundle size
    - Improved Performance
    - Efficient Dependency Management


### Named import

If you want to name your import to something, write the name just before the double quotes of that import.

```go
import (
    foo "net/http"
)
```

- Notes: Go compiler and linker are smart enough to import only the required parts, i.e. only the parts that we have used in our program from those imported packages into the final executable and how that happens is through *Tree Shaking*.

- **Tree Shaking** : Technique used to eliminate the dead or unused code from the final executable or the final bundle, thereby reducing it's size and improving performance of the final bundle or executable.


- During the build process, tree shaking statically analyzes the code base to determine which modules and functions are directly imported and used. Unused modules and functions identified during static analysis are labelled as `dead code`. Tree Shaking then removes these unused segments from the final output optimizing the bundle or executable size.

- eg: React coupled with tools like Webpack and Roll-up employs tree shaking to remove unused components and utility functions from the Javascript bundle. And this optimization is crucial for large scale react applications.

- Tree shaking minimizes the size of executables binaries or the final bundles which is critical for optimizing load times and improving runtime performance of our executable files. Smaller executables lead to faster load times and enhanced runtime efficiency benefitting both developers and end-users. 

- Developers can import the entire library without worry about overhead of unused code because tree-shaking trims the unnecessary parts during the build process.

- The import statement in go plays a pivotal in integrating external functionalities while ensuring that only the necessary parts contribute to the executable.

<br/>
<br/>

## Data Types

- Integers
- Floating Point Numbers
- Complex Numbers
- Booleans
- Strings
- Constants
- Arrays
- Structs
- Pointers
- Maps
- Slices
- Functions
- Channels
- JSON
- Text and HTML Templates
<br/>

- Variables declared without an explicit initialization are assigned a default zero value based on their type.
    - Numeric types are given a value of zero
    - boolean types are defaulted to False
    - String type is an empty string by default
    - pointers, slices, maps, functions and structs are initialized with `nil` value.


## Variables

- the `type` of the is optional if we are initializing the variable otherwise we have to declare the variable with a particular type.

- we can use the gofer symbol (`:=`) to initialize the variable.
    ```go
    count := 10
    lastName := "Smith"
    ```

- This is called type inference in go, allowing the variables to be initalized without explicitly specifying the type. The type is inferred from the assigned value.

- Variables in go have `block scope` meaning that they are accessible only within the block they are declared.

- It's kind of a rule in Go that : `gofer` notation can only be used within functions to declare and initialize variables locally. It is intented for local variables initialization within functions only.

- If we are making a package level variable (global variable) then we cannot use the gopher notation.

- global variable is only limited to the package scope. Outside the package we cannot use that variable.

- variables live within their scope.

- Variables in go provide a flexible and powerful way to manage data within programs.


## Constants

- Constants must be initialized with values that can be determined at compile time. This typically includes literals and expressions that can be evaluated without runtime computations.

- Go supports both `typed` and `untyped` constants.
- Untyped constants are constants without a specified type until they are assigned to a value. They can be used in contexts that require a specific type, and go will automatically infer the approproate type.

- NOTE: There is no short declaration for constants.

- `const block` : We can group related constants together using this const block to make our life easier.

- constants in go provide a mechanism for defining immutable values that remain consistent throughout the execution of the program.


<br />

## Arithmetic Operators

- Basic Arithmetic Operators
    - Addition +
    - Subtraction -
    - Multiplication *
    - Division /
    - Remainder (Modulus) %

- Operator Precedence
    1. Parentheses ()
    2. Multiplication *, Division /, Remainder %
    3. Addition +, Subtraction -

- Overflow
- Underflow

- Why be mindful of overflow and underflow ?
    - Program Stability
    - Data Integrity
    - Type Safety

- Mitigation Strategies
    - Range Checking
    - Type Conversion
    - Error Handling

- Be mindful of potential overflow and underflow issues, especially when dealing with large numbers.

- Overflow occurs when the result of a computation exceeds the maximum value that can be stored in a given numeric data-type. Overflow results in the value wrapping around to the minimum value for signed integers or causing unexpected behaviour for unsigned integers. eg: if you add two large integers and the result exceeds the maximum value represented by that integer type, overflow occurs.

- Similarly, Underflow occurs when the result of a compilation is smaller than the minimum value that can be stored in a given numeric data type. This is more relevant for floating point numbers, where underflow can lead to loss of precision or significant digits in calculations involving very small values.

- This needs to be taken care of when we are working on applications that are involved in scientific calculations, and where calculated values are big numbers.

<br/>

## For Loop

- For loop is a fundamental control structure that allows you to repeatedly execute a block of code based on a condition.

- Syntax
    ```go
    for initialization; conditon; post {
        // Codeblock to be executed repeatedly
    }
    ```

- Initialization: Executed before the first iteration. Typically used to initalize loop variables.

- Conditon: Evaluate before each iteration. If false the loop terminates

- Post: Executed after each iteration. Usally increments or updates loop variables.

    ```go
    for i=1; i<=5; i++ {
        // Code block to be executed repeatedly
    }
    ```
- Break: Terminates the loop immediately, transferring control to the next statement after the loop.

- Continue: Skips the current iteration and moves to the next iteration of the loop.

-   `%v` -> general value
    `%d` -> specific integers


<br/>

## Operators

- Logical Operators
    - ! : logical NOT
    - || : logical OR
    - && : logical AND

- Bitwise Operator
    - & : bitwise AND
    - | : bitwise OR
    - ^ : bitwise XOR
    - &^ : bitwise AND NOT
    - << : left shift
    - >> : right shift

- Comparison Operators:
    - == : equal
    - != : not equal
    - <  : less than
    - <= : less than or equal to
    - >  : greater than
    - >= : greater than or equal to

## Conditions: if else

- If else condition are essential for controlling the flow of execution based on different conditions. They allow you to create decision making logic within your programs, enabling you to execute specific block of code based on whether certain conditions evaluate to true or false.