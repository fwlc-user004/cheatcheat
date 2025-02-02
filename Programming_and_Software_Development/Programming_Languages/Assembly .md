# 🏆 Ultimate Assembly Language Cheat Sheet

---

## 📌 1. Introduction to Assembly Language

Assembly language is a **low-level programming language** that is closely related to machine code. It is used for **system programming, embedded systems, and performance-critical applications**.

### 🔹 Basic Structure of an Assembly Program (x86 NASM Syntax)
```assembly
section .data
    message db "Hello, Assembly!", 0

section .text
    global _start

_start:
    mov rax, 1        ; syscall number for sys_write
    mov rdi, 1        ; file descriptor (stdout)
    mov rsi, message  ; message address
    mov rdx, 16       ; message length
    syscall           ; call kernel

    mov rax, 60       ; syscall number for exit
    xor rdi, rdi      ; return 0
    syscall
```

---

## 📌 2. Registers

### 🔹 General Purpose Registers (x86-64)
| Register | Purpose |
|----------|---------|
| `RAX` | Accumulator |
| `RBX` | Base register |
| `RCX` | Counter register |
| `RDX` | Data register |
| `RSI` | Source index |
| `RDI` | Destination index |
| `RSP` | Stack pointer |
| `RBP` | Base pointer |

### 🔹 Segment Registers
| Register | Purpose |
|----------|---------|
| `CS` | Code segment |
| `DS` | Data segment |
| `SS` | Stack segment |
| `ES` | Extra segment |
| `FS` | Additional segment |
| `GS` | Additional segment |

---

## 📌 3. Basic Instructions

### 🔹 Data Movement
```assembly
mov eax, 10    ; Move 10 into EAX
mov ebx, eax   ; Copy EAX into EBX
xchg eax, ebx  ; Swap EAX and EBX
```
### 🔹 Arithmetic Operations
```assembly
add eax, 5    ; Add 5 to EAX
sub eax, 3    ; Subtract 3 from EAX
mul ebx       ; Multiply EAX by EBX (result in EAX and EDX)
div ebx       ; Divide EAX by EBX (quotient in EAX, remainder in EDX)
```
### 🔹 Logical Operations
```assembly
and eax, 0xF0  ; Bitwise AND
or eax, 0x0F   ; Bitwise OR
xor eax, eax   ; Bitwise XOR (clear EAX)
not eax        ; Bitwise NOT
shl eax, 2     ; Shift left by 2 bits
shr eax, 2     ; Shift right by 2 bits
```
### 🔹 Comparison and Jumps
```assembly
cmp eax, ebx    ; Compare EAX and EBX
je  label       ; Jump if equal
jne label       ; Jump if not equal
jg  label       ; Jump if greater
jl  label       ; Jump if less
jmp label       ; Unconditional jump
```

---

## 📌 4. Stack Operations

### 🔹 Stack Push/Pop
```assembly
push eax    ; Push EAX onto the stack
pop ebx     ; Pop value from stack into EBX
```

### 🔹 Function Calls and Return
```assembly
call my_function  ; Call a function
ret               ; Return from function
```

---

## 📌 5. System Calls (Linux x86-64)

### 🔹 System Call Table (Common Syscalls)
| Syscall Number | Function |
|---------------|----------|
| `60` | Exit |
| `1`  | Write |
| `0`  | Read |
| `2`  | Open |
| `3`  | Close |

### 🔹 Example: Exit Program
```assembly
mov rax, 60    ; syscall number for exit
xor rdi, rdi   ; return 0
syscall
```

### 🔹 Example: Writing to Standard Output
```assembly
section .data
    message db "Hello, world!", 13, 10

section .text
    global _start

_start:
    mov rax, 1    ; syscall number for sys_write
    mov rdi, 1    ; file descriptor (stdout)
    mov rsi, message
    mov rdx, 13   ; message length
    syscall

    mov rax, 60   ; syscall number for exit
    xor rdi, rdi
    syscall
```

---

## 📌 6. Calling Conventions (x86-64 Linux)

### 🔹 Function Calling Registers
| Register | Purpose |
|----------|---------|
| `RDI` | 1st argument |
| `RSI` | 2nd argument |
| `RDX` | 3rd argument |
| `RCX` | 4th argument |
| `R8`  | 5th argument |
| `R9`  | 6th argument |

### 🔹 Example: Function Call
```assembly
section .text
    global _start

_start:
    mov rdi, 42     ; First argument
    call my_function
    mov rax, 60     ; Exit syscall
    xor rdi, rdi
    syscall

my_function:
    add rdi, 10     ; Add 10 to first argument
    ret
```

---

## 📌 7. Memory Management

### 🔹 Allocating and Deallocating Memory (sys_brk syscall)
```assembly
mov rax, 12    ; syscall number for brk
mov rdi, 0     ; get current break
syscall

add rax, 4096  ; allocate 4KB
mov rdi, rax
mov rax, 12
syscall
```

---
