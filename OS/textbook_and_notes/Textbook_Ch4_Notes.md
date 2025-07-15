# Chapter 4

## Chapter Aims

Chapter 4 dives into assembly code, with its main focus on trying to relate
how close C is to assembly, working up to how it maps together.

---

## objdump Command

It begins with explaining the `objdump` command. This displays information 
about object files (those that have been compiled, for example,
if we compile a program called hello.c into an executable called 
`hello`, objdump allows us to see how the high level source code maps to 
the assembly). 

For this to work, I wrote the following code in C:

```C
    #include <stdio.h>

    int main(){

        printf("Hello World!");
        return 0;
    }

```

I then compiled `hello.c` through:

    `$ clang hello.c -o hello`

When following the next steps in the textbook, we then run the following command:

```bash

   $ objdump -d hello

```

This gives us the following output:

```asm

hello:     file format elf64-x86-64


Disassembly of section .init:

0000000000001000 <_init>:
    1000:       f3 0f 1e fa             endbr64
    1004:       48 83 ec 08             sub    $0x8,%rsp
    1008:       48 8b 05 c1 2f 00 00    mov    0x2fc1(%rip),%rax        # 3fd0 <__gmon_start__@Base>
    100f:       48 85 c0                test   %rax,%rax
    1012:       74 02                   je     1016 <_init+0x16>
    1014:       ff d0                   call   *%rax
    1016:       48 83 c4 08             add    $0x8,%rsp
    101a:       c3                      ret

Disassembly of section .plt:

0000000000001020 <printf@plt-0x10>:
    1020:       ff 35 ca 2f 00 00       push   0x2fca(%rip)        # 3ff0 <_GLOBAL_OFFSET_TABLE_+0x8>
    1026:       ff 25 cc 2f 00 00       jmp    *0x2fcc(%rip)        # 3ff8 <_GLOBAL_OFFSET_TABLE_+0x10>
    102c:       0f 1f 40 00             nopl   0x0(%rax)

0000000000001030 <printf@plt>:
    1030:       ff 25 ca 2f 00 00       jmp    *0x2fca(%rip)        # 4000 <printf@GLIBC_2.2.5>
    1036:       68 00 00 00 00          push   $0x0
    103b:       e9 e0 ff ff ff          jmp    1020 <_init+0x20>

Disassembly of section .plt.got:

0000000000001040 <__cxa_finalize@plt>:
    1040:       ff 25 9a 2f 00 00       jmp    *0x2f9a(%rip)        # 3fe0 <__cxa_finalize@GLIBC_2.2.5>
    1046:       66 90                   xchg   %ax,%ax

Disassembly of section .text:

0000000000001050 <_start>:
    1050:       f3 0f 1e fa             endbr64
    1054:       31 ed                   xor    %ebp,%ebp
    1056:       49 89 d1                mov    %rdx,%r9
    1059:       5e                      pop    %rsi
    105a:       48 89 e2                mov    %rsp,%rdx
    105d:       48 83 e4 f0             and    $0xfffffffffffffff0,%rsp
    1061:       50                      push   %rax
    1062:       54                      push   %rsp
    1063:       45 31 c0                xor    %r8d,%r8d
    1066:       31 c9                   xor    %ecx,%ecx
    1068:       48 8d 3d d1 00 00 00    lea    0xd1(%rip),%rdi        # 1140 <main>
    106f:       ff 15 4b 2f 00 00       call   *0x2f4b(%rip)        # 3fc0 <__libc_start_main@GLIBC_2.34>
    1075:       f4                      hlt
    1076:       66 2e 0f 1f 84 00 00    cs nopw 0x0(%rax,%rax,1)
    107d:       00 00 00

0000000000001080 <deregister_tm_clones>:
    1080:       48 8d 3d 91 2f 00 00    lea    0x2f91(%rip),%rdi        # 4018 <__TMC_END__>
    1087:       48 8d 05 8a 2f 00 00    lea    0x2f8a(%rip),%rax        # 4018 <__TMC_END__>
    108e:       48 39 f8                cmp    %rdi,%rax
    1091:       74 15                   je     10a8 <deregister_tm_clones+0x28>
    1093:       48 8b 05 2e 2f 00 00    mov    0x2f2e(%rip),%rax        # 3fc8 <_ITM_deregisterTMCloneTable@Base>
    109a:       48 85 c0                test   %rax,%rax
    109d:       74 09                   je     10a8 <deregister_tm_clones+0x28>
    109f:       ff e0                   jmp    *%rax
    10a1:       0f 1f 80 00 00 00 00    nopl   0x0(%rax)
    10a8:       c3                      ret
    10a9:       0f 1f 80 00 00 00 00    nopl   0x0(%rax)

00000000000010b0 <register_tm_clones>:
    10b0:       48 8d 3d 61 2f 00 00    lea    0x2f61(%rip),%rdi        # 4018 <__TMC_END__>
    10b7:       48 8d 35 5a 2f 00 00    lea    0x2f5a(%rip),%rsi        # 4018 <__TMC_END__>
    10be:       48 29 fe                sub    %rdi,%rsi
    10c1:       48 89 f0                mov    %rsi,%rax
    10c4:       48 c1 ee 3f             shr    $0x3f,%rsi
    10c8:       48 c1 f8 03             sar    $0x3,%rax
    10cc:       48 01 c6                add    %rax,%rsi
    10cf:       48 d1 fe                sar    $1,%rsi
    10d2:       74 14                   je     10e8 <register_tm_clones+0x38>
    10d4:       48 8b 05 fd 2e 00 00    mov    0x2efd(%rip),%rax        # 3fd8 <_ITM_registerTMCloneTable@Base>
    10db:       48 85 c0                test   %rax,%rax
    10de:       74 08                   je     10e8 <register_tm_clones+0x38>
    10e0:       ff e0                   jmp    *%rax
    10e2:       66 0f 1f 44 00 00       nopw   0x0(%rax,%rax,1)
    10e8:       c3                      ret
    10e9:       0f 1f 80 00 00 00 00    nopl   0x0(%rax)

00000000000010f0 <__do_global_dtors_aux>:
    10f0:       f3 0f 1e fa             endbr64
    10f4:       80 3d 1d 2f 00 00 00    cmpb   $0x0,0x2f1d(%rip)        # 4018 <__TMC_END__>
    10fb:       75 2b                   jne    1128 <__do_global_dtors_aux+0x38>
    10fd:       55                      push   %rbp
    10fe:       48 83 3d da 2e 00 00    cmpq   $0x0,0x2eda(%rip)        # 3fe0 <__cxa_finalize@GLIBC_2.2.5>
    1105:       00
    1106:       48 89 e5                mov    %rsp,%rbp
    1109:       74 0c                   je     1117 <__do_global_dtors_aux+0x27>
    110b:       48 8b 3d fe 2e 00 00    mov    0x2efe(%rip),%rdi        # 4010 <__dso_handle>
    1112:       e8 29 ff ff ff          call   1040 <__cxa_finalize@plt>
    1117:       e8 64 ff ff ff          call   1080 <deregister_tm_clones>
    111c:       c6 05 f5 2e 00 00 01    movb   $0x1,0x2ef5(%rip)        # 4018 <__TMC_END__>
    1123:       5d                      pop    %rbp
    1124:       c3                      ret
    1125:       0f 1f 00                nopl   (%rax)
    1128:       c3                      ret
    1129:       0f 1f 80 00 00 00 00    nopl   0x0(%rax)

0000000000001130 <frame_dummy>:
    1130:       f3 0f 1e fa             endbr64
    1134:       e9 77 ff ff ff          jmp    10b0 <register_tm_clones>
    1139:       0f 1f 80 00 00 00 00    nopl   0x0(%rax)

0000000000001140 <main>:
    1140:       55                      push   %rbp
    1141:       48 89 e5                mov    %rsp,%rbp
    1144:       48 83 ec 10             sub    $0x10,%rsp
    1148:       c7 45 fc 00 00 00 00    movl   $0x0,-0x4(%rbp)
    114f:       48 8d 3d ae 0e 00 00    lea    0xeae(%rip),%rdi        # 2004 <_IO_stdin_used+0x4>
    1156:       b0 00                   mov    $0x0,%al
    1158:       e8 d3 fe ff ff          call   1030 <printf@plt>
    115d:       31 c0                   xor    %eax,%eax
    115f:       48 83 c4 10             add    $0x10,%rsp
    1163:       5d                      pop    %rbp
    1164:       c3                      ret

Disassembly of section .fini:

0000000000001168 <_fini>:
    1168:       f3 0f 1e fa             endbr64
    116c:       48 83 ec 08             sub    $0x8,%rsp
    1170:       48 83 c4 08             add    $0x8,%rsp
    1174:       c3                      ret

```

What dictates what is returned here is the `-d` option which only displays assembled contents of executable sections. An executable section is that of a block of memory that, for example, contains program code, as a code section is that which is executable. 

Other sections, such as non-executable sections, are that of .data or .bss (for storing program data), and debug sections. However, these are NOT displayed. 

The chapter then goes onto explain other flags of objdump, I have compiled these as a list:

- `-D`: Displays assembly contents of ALL sections, not just executable sections (i.e. not just program code)

- `-S`: Displays both source code and assembly in the output; MUST compile the code using the -g flag however (this generates debug information)

- `-M`: Allows the output syntax to be modified. For example, the default syntax of objdump is AT&T syntax, if we want an intel syntax we can write

    `$ objdump -M intel -D hello`

---

## Reading Assembly Code

Take the following disassembled instruction:

- `4004d6:` `55` `push rbp` `#This is an assembly comment`

1. The first column is that of the assembly instruction's address. In our example, the address is 0x4004d6 in full

2. The second column is the assembly instruction in raw hex values. This equates to 0x55

3. The third column is the actual assembly instruction. However, this may or may not be significant as if we use the `-D` flag then our output will contain all sections, not just executable sections. Thus, what we may be looking at is a data section, as objdump can't differentiate between what is code and what is not, and it will just translate every hex value into an assembly instruction. 

In our example, our instruction is `push %rbp` which saves the old base pointer onto the stack which is normally used at the start of a function to save the previous frame's base pointer. This helps keep track of where local variables and function arguments are.
 
4. The fourth column is optional, and this allows for the addition of comments, which are done using a `#`.

5. Another addition which may be found when reading disassembled sections is a **label**, which is simply a name that is given to an assembly instruction. This simply denotes what the section is doing to someone who may be reading it. Can think of this as a *doc_string* like in python. A **label is a name of a memory address**


## Assembling Assembly

To do this, the textbook ops for the **nasm** assembler. We begin with the following example (which has been stored in `test.asm`):

```asm
    jmp eax
```

Then, we run the following:

```bash
    $ nasm -f bin test.asm -o test
```

Much like clang, put in our file and express what we want our output to be with `-o`. The `-f` flag here allows us to express the file format of the output. In the example this is a flat binary file (as we have used `bin`) without additional information included. That is, the assembly is translated to machine code without additional overheads from metadata. 

To view the resultant compiled machine code, we can use the `hd` (*hex dump*) command:

```bash
    $ hd test
```

For our program, we get the following:

```
00000000 66 ff e0   |f..|
00000003
```






