shl ax, 1

mov rax, 0x1234

xor rax, 0xffffffff
not rax

mov rcx, 0
cmp eax, edx
cmovg rcx, 1

^ ist XOR in C