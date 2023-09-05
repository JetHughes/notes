---
title: "08-intro-to-c"
aliases: 
tags: 
- lecture
- cosc204
sr-due: 2024-08-02
sr-interval: 368
sr-ease: 230
---

Developed 1972 for Unix

- widely used
	- compilers esxist for most OSs and architectiures
- diverse use
	- OSs, device drivers, protocol stacks
	- less so for application software
- low level
	- language features map to CPU features 
- not Object Oriented
	- no classes etc

> “C is an imperative procedural language supporting structured programming, lexical variable scope, and recursion, with a static type system. It was designed to be compiled to provide low-level access to memory and language constructs that map efficiently to machine instructions, all with minimal runtime support. Despite its low-level capabilities, the language was designed to encourage cross-platform programming. A standards-compliant C program written with portability in mind can be compiled for a wide variety of computer platforms and operating systems with few changes to its source code.” - wikipedia

``` c
#include <stdio.h>

int main(int argc, const char *argv[])
{
	puts("Hello World");
	return 0;
}
```

# \#include
java uses .class files, C uses .c and .h
- .c for implementation
- .h for extern declarations (similar to `public`)

java uses `import`, C uses `#include`

``` c
#include <stdio.h>
#include "myfile.h"
```

- `#include` literally includes the file with the given name right there into the file eing compiled
- in `hello_world.c` we include `stdio.h` so we can call `puts()`

# Routines
``` c
int main(int argc, const char *argv[])
{

}
```

routines can be scoped to just the source code file
- `static int eleven(void`

routines must be declared bfore being used
- `extern int eleven(void):`

# if, const, for, while, do, case etc same as java

# Types

```
char
float, double
int, short, long
signed, unsigned
void
```

![integer ranges](https://i.imgur.com/5gmgTer.png)

## sizeof
- to find out size of any type (built-in or user defined)

## stdint
![stdint.h](https://i.imgur.com/7W6T0y5.png)

## Structs
- like classes but without methods
- all fields public
- you can have structs in structs

## typedef
- any type can be given a new name using typedef

```
typedef struct
	{
		float x, y, z;
	} coordinate;
```

## static
- the scope of this routine is local to this file
- this variable maintains its value between calls

```
void keeper(void) { 
	static uint64_t times_called = 0; 
	times_called++; 
	printf("Count:%llu\n", times_called); 
}
```

## typecasting
like java
```
uint64_t y = 1024;
unit32_t x = (unit32_t) y;
```

## Keywords to ignore
- auto
	- all local variables are auto
- register
	- deprecated

## keywords to think about
- volatile
	- do not optimize accesses to this variable
		- might be changed by another thread or a harware event
	- you're likely to see this in operating system souce code
	- you're likely to see this in multithreaded programs
