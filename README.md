section .data
    hello db 'Hello World!', 10

section .text
global _start

_start:

    mov rax, 1          
    mov rdi, 1          
    mov rsi, hello      
    mov rdx, 13        
    syscall

    jmp exit_program    

    mov rax, 1
    mov rdi, 1
    mov rsi, hello
    mov rdx, 13
    syscall

exit_program:
    mov rax, 60        
    xor rdi, rdi
    syscall



section .data

lines:                
    line1 db '     _      ',10
    line2 db '    _     ',10
    line3 db '    _     ',10
    line4 db '    _     ',10

line_lengths:
    dq 11, 10, 10, 10  

section .text
global _start

_start:

    mov rbx, 0         

print_loop:
    cmp rbx, 4          
    je  exit_program    

   
    mov rax, 1          
    mov rdi, 1          

    lea rsi, [lines + rbx*13] 

    
    mov rdx, [line_lengths + rbx*8] 

    syscall

    inc rbx             
    jmp print_loop      

exit_program:
    mov rax, 60         
    xor rdi, rdi
    syscall

