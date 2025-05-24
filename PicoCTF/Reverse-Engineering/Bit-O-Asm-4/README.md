
## How to solve

1. ![alt text](image.png)

2. 
```asm
<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a     ; menyimpan nilai 0x9fe1a ke DWORD PTR [rbp-0x4]
<+22>:    cmp    DWORD PTR [rbp-0x4],0x2710      ; membandingkan nilai [rbp-0x4] dengan 0x2710
<+29>:    jle    0x55555555514e <main+37>        ; lompat ke <main+37> jika [rbp-0x4] <= 0x2710 (tidak terjadi, jadi tidak lompat)
<+31>:    sub    DWORD PTR [rbp-0x4],0x65        ; kurangi nilai [rbp-0x4] dengan 0x65
<+35>:    jmp    0x555555555152 <main+41>        ; lompat ke <main+41>
<+37>:    add    DWORD PTR [rbp-0x4],0x65        ; (dilewati karena kondisi lompat tidak terpenuhi)
<+41>:    mov    eax,DWORD PTR [rbp-0x4]         ; pindahkan nilai [rbp-0x4] ke register eax
```


3. 0x9fe1a - 0x65
