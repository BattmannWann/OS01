Chapter 3 covers computer architecture and provides basic definitions:

    - Computer: a hardware device that consists of at least a processor 
      (CPU), a memory device, and input/output interfaces. ALL computers can
      be grouped into either single-purpose (built for specific tasks) or
      general purpose (programmed to emulate various features of 
      single-purpose computers; without modifying its hardware).

    - Server: A general purpose high-performance computer with huge 
      resources to provide large-scale services for large user-bases

    - Desktop Computer: General-purpose computer with an input and output
      system designed for a human user. This normally includes a mouse,
      keyboard, and monitor. 

    - Mobile Computer: Similar to a desktop but with fewer resources and
      is portable. Examples include a phone, laptop, or tablet. 

    - Game Console: Similar to desktop computers but are optimised for
      gaming. 

    - Embedded Computer: A single-board or single-chip computer with
      limited resources designed for integrating into larger hardware 
      devices. 

    - Microcontroller: Embedded computer designed for controlling other
      hardware devices. These are mounted on a chip and are general-purpose
      computers; often with limited resources as they are designed to carry
      out a specialised/specific task. 

These are just some definitions, but to avoid copy and pasting the whole 
chapter, this will conclude the basic definitions segment.


At principle, every computer is designed for an architect from high to 
low level, where we can define computer architecture as follows:

Computer Architecture = Instruction Set Architecture + Computer Organisation + Hardware

Where our equation lists highest to lowest level accordingly. 

We can define the following:

    - Instruction Set: Basic set of commands and instructions that a 
      microprocessor understands and can carry out

    - Instruction Set Architecture (ISA): The design of an environment 
      that implements an instruction set. This includes instructions, 
      registers, interrupts, memory models (how memory is arranged),
      addressing modes, I/O and etc.... We can then think of a CPU as 
      an implementation of an ISA (effectively the implementation of
      an assembly language).

    - Computer Organisation: The functional view of the design of a computer.
      This is often contributed to the Von-Neumann Diagram but as time
      has went on, this has became more complicated. 

    - Von-Neumann Computer: Operates by storing its instructions in 
      main memory, where the CPU repeatedly fetches those instructions 
      into its internal storage for executing, one after the other. 
      This approach is now outdated as is incredibly inefficient as
      fetches from main memory are slow. Newer approaches use caches
      and other memory efficient operations instead. 


What are the devices that a CPU commands?

    - Registers: Hardware components used for high-speed data access
      and communication with other hardware devices.

    Port: Specialised register used for communication with other
          devices. 

    - Memory: A storage device that allows a computer to store information.
              Memory consists of many cells; a byte with its address no. 

    - Bus: A subsystem that transfers data between computer components or
           between computers. Physically, these are just electrical wires.



