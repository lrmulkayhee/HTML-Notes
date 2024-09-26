# Assembly Language Basic Syntax and Grammar Guide

## Overview

Assembly language is a low-level programming language that is closely related to machine code. It provides a way to write instructions that the CPU can execute directly. This guide covers the basic syntax and grammar of assembly language, focusing on registers, instructions, and a simple example.

## Basic Syntax

An Assembly program typically consists of three sections:

1. **Data Section**: Used to declare initialized and uninitialized data or constants.
2. **BSS Section**: Used to declare variables.
3. **Text Section**: Contains the actual code.

### Example

Here is a simple example of an assembly program that writes a message to stdout and then exits:

```assembly
section .data
    msg db 'Hello, world!', 0xA  ; The message to print

section .text
    global _start

_start:
    ; Write the message to stdout
    mov eax, 4          ; syscall number for sys_write
    mov ebx, 1          ; file descriptor 1 is stdout
    mov ecx, msg        ; pointer to the message
    mov edx, 13         ; message length
    int 0x80            ; call kernel

    ; Exit the program
    mov eax, 1          ; syscall number for sys_exit
    xor ebx, ebx        ; exit code 0
    int 0x80            ; call kernel
```

## Registers

Registers are small, fast storage locations within the CPU used to hold data temporarily during execution. Common general-purpose registers include:
- `eax`: Accumulator register
- `ebx`: Base register
- `ecx`: Counter register
- `edx`: Data register

Other types of registers include:
- `esi` and `edi`: Source and destination index registers
- `ebp` and `esp`: Base pointer and stack pointer registers
- `eip`: Instruction pointer register

## Instructions

Instructions are the commands that tell the CPU what operations to perform. Each instruction typically consists of an opcode (operation code) and operands (data or addresses). Common instructions include:
- `mov`: Move data from one location to another
- `add`: Add two values
- `sub`: Subtract one value from another
- `int`: Interrupt, used to make system calls

### Instruction Format

The general format of an assembly instruction is:
```assembly
opcode destination, source
```
#### Example
```assembly
mov eax, 1  ; Move the value 1 into the eax register
add eax, 2  ; Add the value 2 to the eax register
sub eax, 1  ; Subtract the value 1 from the eax register
int 0x80    ; Make a system call
```

## Memory Addressing

Memory addressing in assembly language refers to the way in which the location of data is specified. There are several types of memory addressing modes:

1. **Immediate Addressing**: The operand is a constant value.
    ```assembly
    mov eax, 10  ; Move the constant value 10 into the eax register
    ```

2. **Register Addressing**: The operand is a register.
    ```assembly
    mov eax, ebx  ; Move the value in the ebx register into the eax register
    ```

3. **Direct Addressing**: The operand is a memory address.
    ```assembly
    mov eax, [0x1234]  ; Move the value at memory address 0x1234 into the eax register
    ```

4. **Indirect Addressing**: The operand is a memory address stored in a register.
    ```assembly
    mov eax, [ebx]  ; Move the value at the memory address stored in the ebx register into the eax register
    ```

5. **Indexed Addressing**: The operand is a memory address calculated using a base address and an index.
    ```assembly
    mov eax, [ebx + esi]  ; Move the value at the memory address (ebx + esi) into the eax register
    ```

6. **Base-Indexed Addressing**: The operand is a memory address calculated using a base address, an index, and an optional displacement.
    ```assembly
    mov eax, [ebx + esi + 4]  ; Move the value at the memory address (ebx + esi + 4) into the eax register
    ```

## Control Flow

Control flow instructions in assembly language determine the order in which instructions are executed. Common control flow instructions include:

1. **Jump Instructions**: Used to transfer control to another part of the program.
    - `jmp`: Unconditional jump.
    - `je` / `jz`: Jump if equal / zero.
    - `jne` / `jnz`: Jump if not equal / not zero.
    - `jg` / `jnle`: Jump if greater / not less or equal.
    - `jl` / `jnge`: Jump if less / not greater or equal.

    ```assembly
    jmp label       ; Unconditional jump to 'label'
    je equal_label  ; Jump to 'equal_label' if zero flag is set
    jne not_equal_label  ; Jump to 'not_equal_label' if zero flag is not set
    ```

2. **Loop Instructions**: Used to repeat a block of code a certain number of times.
    - `loop`: Decrement `ecx` and jump if `ecx` is not zero.

    ```assembly
    mov ecx, 10     ; Set loop counter to 10
    loop_start:
    ; Code to repeat
    loop loop_start ; Decrement ecx and jump to 'loop_start' if ecx is not zero
    ```

3. **Call and Return Instructions**: Used to call and return from procedures.
    - `call`: Call a procedure.
    - `ret`: Return from a procedure.

    ```assembly
    call procedure  ; Call 'procedure'
    ; ...
    procedure:
    ; Procedure code
    ret             ; Return from 'procedure'
    ```

## Data Types and Directives

Assembly language supports various data types and directives to define and manipulate data. Common data types include:

- `db` (Define Byte): Defines a byte (8 bits) of data.
- `dw` (Define Word): Defines a word (16 bits) of data.
- `dd` (Define Double Word): Defines a double word (32 bits) of data.
- `dq` (Define Quad Word): Defines a quad word (64 bits) of data.

### Example

```assembly
section .data
    byteVar db 0x1       ; Define a byte variable
    wordVar dw 0x1234    ; Define a word variable
    dwordVar dd 0x12345678 ; Define a double word variable
    qwordVar dq 0x123456789ABCDEF0 ; Define a quad word variable
```

Directives are commands that provide instructions to the assembler. Common directives include:

- `section`: Defines a section of the program (e.g., `.data`, `.bss`, `.text`).
- `global`: Makes a symbol available to the linker.
- `extern`: Declares an external symbol.
- `equ`: Defines a constant value.

### Example

```assembly
section .data
    msg db 'Hello, world!', 0xA  ; Define a message

section .bss
    buffer resb 64  ; Reserve 64 bytes for a buffer

section .text
    global _start

_start:
    ; Code to execute
```

## Input and Output Operations

Input and output operations in assembly language are typically performed using system calls. These system calls interact with the operating system to read from input devices or write to output devices.

### Writing to Standard Output

To write to standard output (stdout), you can use the `sys_write` system call. The following example writes a message to stdout:

```assembly
section .data
    msg db 'Hello, world!', 0xA  ; The message to print

section .text
    global _start

_start:
    mov eax, 4          ; syscall number for sys_write
    mov ebx, 1          ; file descriptor 1 is stdout
    mov ecx, msg        ; pointer to the message
    mov edx, 13         ; message length
    int 0x80            ; call kernel

    mov eax, 1          ; syscall number for sys_exit
    xor ebx, ebx        ; exit code 0
    int 0x80            ; call kernel
```

### Reading from Standard Input

To read from standard input (stdin), you can use the `sys_read` system call. The following example reads input from stdin into a buffer:

```assembly
section .bss
    buffer resb 64  ; Reserve 64 bytes for the buffer

section .text
    global _start

_start:
    mov eax, 3          ; syscall number for sys_read
    mov ebx, 0          ; file descriptor 0 is stdin
    mov ecx, buffer     ; pointer to the buffer
    mov edx, 64         ; number of bytes to read
    int 0x80            ; call kernel

    mov eax, 1          ; syscall number for sys_exit
    xor ebx, ebx        ; exit code 0
    int 0x80            ; call kernel
```

These examples demonstrate basic input and output operations using system calls in assembly language.

## Comments

Comments in assembly language are used to annotate the code and make it more understandable. They are ignored by the assembler and do not affect the execution of the program. In most assembly languages, comments are denoted by a semicolon (`;`).

### Single-Line Comments

Single-line comments start with a semicolon and continue to the end of the line.

```assembly
mov eax, 1  ; Move the value 1 into the eax register
```

### Multi-Line Comments

While assembly language does not have a specific syntax for multi-line comments, you can achieve this by using multiple single-line comments.

```assembly
; This is a multi-line comment
; explaining the following block
; of code.
mov eax, 1
mov ebx, 2
add eax, ebx
```

Using comments effectively can greatly improve the readability and maintainability of your assembly code.
