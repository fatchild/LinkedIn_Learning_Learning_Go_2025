# Go 

## Basics

- Build by Google in 2012
- Based on C
- Similar to C, C++, C# and Java

## Attributes

- Go implements OO
	- Encapsulation with types and structs (entities for complex functionality)
	- Polymorphism with interfaces (deal with one type of object as if it's another type)
	- Inheritance GO DOES NOT HAVE TYPE INHERITANCE
		- Interfaces can be implemented and fullfilled by multiple types

## Go's essential characteristics

- Go is compiled
	- The compiled code can only run on a single operating system
- Go is statically typed
	- Variables have specific types (you don't always have to declare them as they are inferred by the compiler)

## Compilation

You run the source code file as if you are working with an interpreted language.
But the code is actually being compiled to a tmp executable.

When creating an application you will create an executable using the go compilation tool.

Compilation is OS specific.

Applications built with go have a statically linked runtime. When compiled the runtime is included. Therefore the output compiled files is greater than the original source code because the runtime is included. The benefit of this is that the compiled code can run without a virtual machine.

## Object orientated

- Go implements OO, but not as heavily as a language like Java.
- Features of Go's OO implementation include
	- Interfaces, contract which defined a set of functions or methods then a type which implements that interface is required to implement those methods.
	- Definition of types, everything is a type in go and every type implements at least one interface
	- When you add functions to a type they are called methods.
	- Each type can have their own member methods.
	- Create your own data structures in go which can have member fields.
- Go does not have:
	- Type inheritance (no classes), you cannot create inherit supertypes
	- No method or operator overloading, each method or type in go has a specific signature
	- No structured acception handling i.e. no try, catch keywords
		- Errors are returned by functions and conditional logic is used to examine the error
	- No implicit numeric conversions, you have to explicitely type the variable or say where you are getting the data.
		- If you want to convert a value in go you need to wrap it in a function which says that you want it to be a specific type

The reason they decided to create a language where some parts of modern languages are included and some parts are not is to make it as simple as possible. You do not have to remember the rules of the language because they are explicitely typed in front of you.

## Syntax

- Designed as next-gen C
- Borrows syntax from C, Pascal and Oberon
- Go trys to reduce the amount of typing

### Rules

- Go is case sensitive
	- Variable and package names are lower and mixed case
	- Package names should be single words, all lower case
	- Exported functions and fields and initial uppercase characters
- Line feeds implies a semi-colon, so they are not needed most of the time. The lexer deals with this.
- Go makes you put the starting brace on the same line as the statement, because of the rule of the semi-colon.
- Built-in functions member of `builtin`
	- `len(string)` evaluates the length of a string
	- `panic(error)` stops execution, displays error message
	- `recover()` manages the behaviour of a panicking go routine
	- The rest of the built-in functions are found in this documentation (https://pkg.go.dev/builtin)

## The go playground

An in browser go editor and developer environment.

https://go.dev/play/

### Limitations

- Security sandbox, so the app doesn't have access to the outside world
- Cannot host applications
- Fakes the file system
- Always the same time, November 10, 2009 at 11:00pm
	- By using the same date and time value it makes the results determinative
- One source file at a time
	- All logic needs to be in one file

## Course Tracker

- [x] Introduction  
- [ ] 1. Getting Started  
- [ ] 2. Manage Simple Variable Values  
- [ ] 3. Manage Complex Types and Collections  
- [ ] 4. Manage Program Flow  
- [ ] 5. Create Reusable Code  
- [ ] 6. Work With Files and the Web  

## Code Notes

### Basics

#### Hello world

```
package main

import "fmt"

func main() {
	fmt.Println("Hello, world!")
}
``` 

- The package name must be declared
- Go will look for the main function and run it

#### Initializing a module

`go mod init MODULENAME`

MODULENAME can be as simple as main i.e. the package name, or use a unique identifier.
MODULENAME as a unique identifier is usually done by reversing the the domain.

`com.example/hello`

This often the github URL and package location.

The output file will be called `go.mod` and have the name of the module and the current version of go you are using, which will be the minimum version of go which the module requires.

#### Debugging

There seems to be a package called GBD and another called Delve. The recommendation appears to be to use Delve.

`brew install delve`

Here is the 'getting started' documentation on GH (https://github.com/go-delve/delve/blob/master/Documentation/cli/getting_started.md)

##### Basic delve usage

Load the package to be debugged
`dlv debug MODULENAME`

Set a breakpoint - package.function
`break main.main`

Continue to the breakpoint
`continue`
