# 0x19. C - Stacks, Queues - LIFO, FIFO

Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files.

## Monty Interpreter

This is a simple interpreter for Monty Bytecode files written in C. It can read a Monty Bytecode file, interpret its instructions and execute them.

## Project Structure

The project is organized as follows:

```
.
├── monty
├── monty.h
├── execute.c
├── main.c
├── operations:
|  ├── op_push.c
|  ├── op_pall.c
|  ├── op_pint.c
|  ├── op_pop.c
|  ├── op_swap.c
|  ├── op_add.c
|  ├── op_sub.c
|  ├── op_div.c
|  ├── op_mul.c
|  ├── op_mod.c
|  ├── op_pchar.c
|  ├── op_pstr.c
|  └── op_nop.c
├── free_stack.c
└── bytecodes
    ├── 00.m
    ├── 01.m
    ├── ....
    ├── ....
    ├── ....
    └── 12.m
```

`monty:` the compiled executable file.

`monty.h:` the header file containing function prototypes, definitions and struct declarations.

`execute.c:` the file containing the execute_opcode() function that determines the opcode to be executed.

`main.c:` the file containing the main() function that reads the bytecode file and executes the opcodes.

`operations:` these are files containing the functions for each opcode (push(), pint(), pop(), swap(), add(), nop()).

`stack.c:` the file containing the stack functions (stack_len(), push_stack(), pop_stack(), free_stack()).

`bytecodes:` a folder containing the bytecode files to be executed by the monty program.

### Installation

To install and run the Monty Interpreter, follow these steps:

- Clone this repository: `git clone https://github.com/Mouadnait/monty`

- Change into the monty directory: `cd monty`

- Compile the interpreter: `gcc -Wall -Werror -Wextra -pedantic *.c -o monty`

- Run the interpreter: `./monty <filename>.m`
  - Replace `<filename>` with the name of the file containing the Monty code to execute.

### Usage

The Monty Interpreter takes a single argument, which is the path to a Monty Bytecode file. The file should contain instructions for the interpreter to execute, one per line.

All the files are compiled in the following form:

```
 gcc -Wall -Werror -Wextra -pedantic *.c -o monty.

```

To run the program:

```
 ./monty bytecode_file
```

Available operation codes:

| Opcode | Description                                                                                                                                                                                        |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| push   | Pushes an element to the stack. e.g (push 1 # pushes 1 into the stack)                                                                                                                             |
| pall   | Prints all the values on the stack, starting from the to of the stack.                                                                                                                             |
| pint   | Prints the value at the top of the stack.                                                                                                                                                          |
| pop    | Removes the to element of the stack.                                                                                                                                                               |
| swap   | Swaps the top to elements of the stack.                                                                                                                                                            |
| add    | Adds the top two elements of the stack. The result is then stored in the second node, and the first node is removed.                                                                               |
| nop    | This opcode does not do anything.                                                                                                                                                                  |
| sub    | Subtracts the top two elements of the stack from the second top element. The result is then stored in the second node, and the first node is removed.                                              |
| div    | Divides the top two elements of the stack from the second top element. The result is then stored in the second node, and the first node is removed.                                                |
| mul    | Multiplies the top two elements of the stack from the second top element. The result is then stored in the second node, and the first node is removed.                                             |
| mod    | Computes the remainder of the top two elements of the stack from the second top element. The result is then stored in the second node, and the first node is removed.                              |
| #      | When the first non-space of a line is a # the line will be trated as a comment.                                                                                                                    |
| pchar  | Prints the integer stored in the top of the stack as its ascii value representation.                                                                                                               |
| pstr   | Prints the integers stored in the stack as their ascii value representation. It stops printing when the value is 0, when the stack is over and when the value of the element is a non-ascii value. |
| rotl   | Rotates the top of the stack to the bottom of the stack.                                                                                                                                           |
| rotr   | Rotates the bottom of the stack to the top of the stack.                                                                                                                                           |
| stack  | This is the default behavior. Sets the format of the data into a stack (LIFO).                                                                                                                     |
| queue  | Sets the format of the data into a queue (FIFO).                                                                                                                                                   |

### Examples

Example 1

```
    push 1
    push 2
    push 3
    pall
    pop
    pall
    pop
    pall
    pop
    pall
```

Output

```
    3
    2
    1
    2
    1
    1
```

Example 2

```
    push 1
    push 2
    push 3
    add
    pall
```

Output

```
    5
```
