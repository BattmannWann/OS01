# OS01

## Purpose
This repository is to track my progress on following the os01 textbook which can be found here: [OS01 Github Page](https://github.com/tuhdo/os01). Its purpose is to help an individual self-learn how to build an operating system from scratch. 

I will upload any relevant notes and code that I produce as an outcome of completing this textbook.


## Current Stage
I am currently on chapter 4 of this textbook

## Additional Reading 
This textbook encourages the reader to read the following:

- Intel® 64 and IA-32 Architectures Software Developer’s Manuals
- 

## Textbook
The textbook can be found here: [Textbook Page](https://github.com/tuhdo/os01/blob/master/Operating_Systems_From_0_to_1.pdf)

To provide specific details of what this textbook covers, please see the following excerpts (*Page 10-13*):

**What you will learn in this book**

- How to write an operating system from scratch by reading hardware
datasheets. In the real world, you will not be able to consult Google
for a quick answer.

- Write code independently. It’s pointless to copy and paste code. Real
learning happens when you solve problems on your own. Some examples are provided to help kick start your work, but most problems are
yours to conquer. However, the solutions are available online for you
after giving a good try.

- A big picture of how each layer of a computer related to each other,
from hardware to software.

- How to use Linux as a development environment and common tools
for low-level programming.

- How a program is structured so that an operating system can run.

- How to debug a program running directly on hardware with gdb and
QEMU.

- Linking and loading on bare metal x86_64, with pure C. No standard
library. No runtime overhead.

---

**What this book is not about**

- Electrical Engineering: The book discusses some concepts from
electronics and electrical engineering only to the extent of how software operates on bare metal.

- How to use Linux or any OS types of books: Though Linux
is used as a development environment and as a medium to demonstrate
high-level operating system concepts, it is not the focus of this book.

- Linux Kernel development: There are already many high-quality
books out there on this subject.

- Operating system books focused on algorithms: This
book focuses more on actual hardware platform - Intel x86_64 - and
how to write an OS that utilizes of OS support from the hardware platform.
The organization of the book

---

**Part 1 provides a foundation for learning operating system.**

- Chapter 1 briefly explains the importance of domain documents.
Documents are crucial for the learning experience, so they deserve
a chapter.

- Chapter 2 explains the layers of abstractions from hardware to software. The idea is to provide insight into how code runs physically.
  
- Chapter 3 provides the general architecture of a computer, then introduces a sample computer model that you will use to write an
operating system.

- Chapter 4 introduces the x86 assembly language through the use
of the Intel manuals, along with commonly used instructions. This
chapter gives detailed examples of how high-level syntax corresponds
to low-level assembly, enabling you to read generated assembly code
comfortably. It is necessary to read assembly code when debugging
an operating system.

- Chapter 5 dissects ELF in detail. Only by understanding how the
structure of a program at the binary level, you can build one that
runs on bare metal.

- Chapter 6 introduces gdb debugger with extensive examples for commonly used commands. After acquainting the reader with gdb, it
then provides insight on how a debugger works. This knowledge is
essential for building a debuggable program on the bare metal.

---

**Part 2 presents how to write a bootloader to bootstrap a kernel**. 

Hence the name “Groundwork”. After mastering this part, the reader can continue with the next part, which is a guide for writing an operating system. However, if the reader does not like the presentation, he or she
can look elsewhere, such as [OSDev Wiki:](http://wiki.osdev.org/).

- Chapter 7 introduces what the bootloader is, how to write one in
assembly, and how to load it on QEMU, a hardware emulator. This
process involves typing repetitive and long commands, so GNU Make
is applied to improve productivity by automating the repetitive parts
and simplifying the interaction with the project. This chapter also
demonstrates the use of GNU Make in context.

- Chapter 8 introduces linking by explaining the relocation process
when combining object files. In addition to a bootloader and an operating system written in C, this is the last piece of the puzzle required for building debuggable programs on bare metal, including
the bootloader written in Assembly and an operating system written in C.

---

**Part 3 provides guidance on how to write an operating system**
You should implement an operating system on your own and be proud of
your creation. The guidance consists of simpler and coherent explanations of necessary concepts, from hardware to software, to implement
operating systems: from 0 to 1 vii
the features of an operating system. Without such guidance, you will
waste time gathering information spread through various documents
and the Internet. It then provides a plan on how to map the concepts

