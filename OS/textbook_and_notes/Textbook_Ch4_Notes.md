Chapter 4 dives into assembly code, with its main focus on trying to relate
how close C is to assembly, working up to how it maps together.

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