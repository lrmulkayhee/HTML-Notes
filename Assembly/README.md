# Assembly Language Notes

This directory contains beginner notes for Assembly language.

## Contents

- [Introduction](#introduction)
- [Setup](#setup)
- [Basic Syntax](#basic-syntax)
- [Projects](#projects)
- [Tutorials](#tutorials)
- [Resources](#resources)

## Introduction

Assembly language is a low-level programming language that is specific to a computer architecture. It is used to write programs that are closely related to the machine code instructions executed by the CPU.

## Setup

1. **Install an Assembler**: You need an assembler to convert assembly code into machine code. Popular assemblers include NASM (Netwide Assembler) and MASM (Microsoft Macro Assembler).
2. **Set Up Your Environment**: Configure your development environment to use the assembler. This may involve setting up paths and environment variables.

## Basic Syntax

Assembly language syntax varies between different assemblers and architectures. Here is a basic example for x86 architecture using NASM:

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