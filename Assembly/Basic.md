# Basic Syntax of Assembly Language

## Registers

Registers are small storage locations within the CPU. Common registers include `eax`, `ebx`, `ecx`, and `edx`.

## Instructions

Instructions are the commands that tell the CPU what to do. Examples include `mov`, `add`, `sub`, and `int`.

### Example

```assembly
section .data
    msg db 'Hello, World!', 0

section .text
    global _start

_start:
    ; Write the message to stdout
    mov eax, 4
    mov ebx, 1
    mov ecx, msg
    mov edx, 13
    int 0x80

    ; Exit the program
    mov eax, 1
    xor ebx, ebx
    int 0x80