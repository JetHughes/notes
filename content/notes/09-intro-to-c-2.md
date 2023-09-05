---
title: "09-intro-to-c-2"
aliases: 
tags: 
- cosc204
---

# Variables and Pointers

```
va memory[3]
*va memory[memory[3]]
**va memory[memory[memory[3]]]
```

`*` is known as **dereferncing**
`**` is known as **double-dereferncing**

## Names and places
names are allocated to emmory locations of declaration

`&b;` wherever in memory b is stored

## Why Pointers
- abstractions
	- dont need to know which "object" to manipulate
- ability to change a parameter
- multiple return values from a routine
- efficiency
	- dont need to copy anything to pass a pointer

## Call by value
- The value of the variable is passed to the called routine.
- changes to the parameter do not propogate to the caller

## Call by address
- address of parameter is passed to the rountine
- changes do propogate back to the caller
- more efficient because we only need to pass a pointer and not a value

### Multiple results
- c routine can return at most one value
- you can use input parameters which are pointers for "returning" results

### Arrays
- strings
	- terminated by "\0"
- argc, argv[]
	- length specified
- null terminated
	- array of pointers

### Pointer arithmetic
- ++ move a pointer fowards in an array
- -- move a pointer back in an array
- these operations are "type aware" and increment (the pointer) by the size of the elements of the array