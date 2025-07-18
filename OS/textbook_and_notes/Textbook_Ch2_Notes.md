This chapter is headed with the title:
    "From hardware to software: Layers of abstraction"

Which very nicely summarises the contents of this chapter, which discuss,
from the bottom up, how a computing system is built. Each section can be
abstracted into a series of layers, with the main idea that each builds
up from the layer below. 


The first sort of layer involves the understanding that there 
is need of physical implementation of a bit, a requirement of any 
electronic device. 

When we write software, we are indirectly manipulating electrical currents
through the hardware found in our device. The start of this comprehension
always lies with the definition of binary, 1's and 0's, as we are told
this is all a computer understands. While this is true, it is a much
simplified definition as it does not cover how this actually happens.

This is where transistors come into play. Transistors, as described by
the textbook, tells us that "a transistor is just a resistor whose values
can vary based on an input voltage". Therefore, utilising this property, 
we can use a transistor to amplify current (this has the effect of 
more voltage and less resistance) or as a switch to electrical signals 
(on or off), basing its actions from a voltage level. 

This is the basis of our 0-off 1-on premise, where Bit 0 is represented
by 0v (no electron flow), and Bit 1 is +3.5v to +5.0v (an electron flow).


Transistors are realised through MOSFET Transistors 
(Metal-Oxide-Semiconductor Field-Effect) which are incredibly efficient,
on comparison to a basic transistor. 


The second part to this chapter discusses logic gates, and how computers 
are able to compute and use bit-wise logic. To describe logic gates, we
use the language of Boolean Algebra. 

It was proven, by Charles Sanders Pierce, that either Boolean function of
NOR or NAND is enough to implement ALL other logic gates (OR, AND, XOR etc..)

Logic gates and digital circuits are themselves implemented using a CMOS Circuit 
(Complementary MOSFET), which consist of two complementary NMOS and PMOS 
transistors:

    - MOSFET (Recap): MOSFET stands for Metal-Oxide-Semiconductor 
                      Field-Effect Transistor. These are electronic 
                      switches that control the flow of electricity in 
                      a circuit. 

    - Complimentary comes from the fact that there are two types
      of MOSFET used in CMOS

      1. NMOS, which conducts when the input is high (the "on-signal")
      2. PMOS, which conducts when the input is low (the "off-signal")

      Which are used together in a pair; one turns on when the other turns
      off. 

Why is CMOS Popular:

    - Low Power Consumption: As one transistor is always off, there is very
      little current flow, with the exception when switching.

    - High Noise Immunity: Less sensitive to small voltage changes (noise)

    - Scalable: Easy to minaturise and pack millions onto a chip

What do the N and P Stand For?

    - The N in NMOS is for "N-Type" which refers to the type of 
      semiconductor material used; in this case it has extra electrons 
      (Negative charge carries, hence NMOS). It connects the output
      to ground when it's on (ON when gate = 1, OFF when gate = 0)

    - The P in PMOS is for "P-Type" which means the material has holes
      (Positive charge carriers). A PMOS transistor turns on (conducts)
      when a low voltage (logic 0) is applied to its gate. It connects
      the output to Vdd (positive voltage) when on 
      (ON when gate = 0, OFF when gate = 1)


The simplest CMOS circuit is an invertor, which is known as a NOT gate:

    =========
    | 0 | 1 |
    | 1 | 0 |
    =========

An implemented circuit with its wires and transistors is stored physically
in a package known as a chip; a substrate that an integrated circuit is 
etched onto. 

NOTE: A chip may also refer to a completely packaged integrated circuit
in the consumer market, so context is required when talking about a chip.


The next layer describes what we call Machine Language. Machine language
is a collection of unique bit patterns that a device can identify and use
to perform a corresponding action. 

This is how we begin to program in its simplest form. Instead of working
with binary itself, we can utilise machine language to speed up development.

A machine instruction is a unique bit pattern that a device can identify. 
In a computing device, a device with its language is called a CPU 
(Central Processing Unit), which is responsible for controlling all 
and any process. 

  - Example bit patterns, in x86 architecture are
      
      10100000 telling a CPU to add two numbers, 
      or 000000101 to halt a computer


How does the computer know what to do?

Essentially, each instruction is actually a small circuit that implements 
said instruction. This can be compared to a function in a programming
language, where it is called during the program by its identifier. This is
practically the same as what happens with a bit pattern, a function inside
the CPU. 


The next layer up is Assembly Language. Assembly takes the bit patterns
one step further, acting as a "symbolic representation of binary machine
code". 

As we can see, each step of abstraction is actually a method to make 
programming more efficient. So, instead of having to write a bunch
of 1s and 0s, a programmer can instead write identifiers:

  - For example, instead of writing 000000101, the programmer could
    now just write hlt. 

Each identifier is simply a mapping of binary. Using a lookup table,
the CPU can process hlt or other instructions into their binary format.

Here are some assembly instructions and their mappings:

  - [or <op1>, <op2>] or accepts two 4-bit operands, which corresponds
    to a 4-input OR gate device = Binary Code 00

  - [nand <op1>, <op2>] here, nand accepts two 4-bit operands, which
    corresponds to, for example, a single chip (in the textbook, the
    example chip is that of a 74HC00) = Binary Code 01

Each binary code is referred to as an operation code (opcode for short).
As such, when deciphering assembly, we see that opcodes come at the start
of each and every instruction, which our CPU is able to take advantage of:

  - nand 1100, 1100 corresponds to the binary string
      0011001100 

To handle how to proceed, a CPU is equipped with a decoder, which taking 
the opcode will decide which circuit is appropriate to use. 

We can summarise this process that a computer takes into the 

              FETCH -> DECODE -> EXECUTE 

cycle; Fetch an instruction from a storage device,
       Decode the instruction,
       Execute the instruction.

We can add more instructions by adding more devices and allocating 
more opcodes for the instructions, then update our encoder to deal with 
the amendments. 


The next layer from assembly language is a PROGRAMMING LANGUAGE. 

Over time, patterns emerged from assembly code that developers were able
to take advantage of; instead of constantly repeating the same code, why 
not EXTRACT out and abstract. Thus, programming languages were born. 

A programming language is yet another method to make programming faster
and more efficient. Our statements are translated into assembly, 
then assembly into machine code. The program that achieves this is called
a COMPILER. 

An important message from this section of the textbook is that, the more
we abstract and move away from hardware, the slower the code runs. 

What this is saying is that, the higher level a programming language, the
more underlying mechanisms are required to translate/compile our code 
into machine code. High level languages are efficient for solving a problem
domain, but less efficient for manipulating the underlying hardware; which
is a concept that higher level languages aim to avoid and even prevent the
programmer from doing. This is why there exists so many programming languages,
as they have been specifically designed to smooth out the job that a programmer
needs to perform. 

If they are interested in very low-level and precise performance of a machine,
a programmer would be more likely to use a language such as C or go straight
to assembly. Otherwise, they would use a language such as Python or Java,
to tackle more higher level problems, such as creating a website.


The last section of this chapter explains the idea of abstraction in more 
depth, along with its advantages and disadvantages.

To expand on our definition of abstraction above, all it essentially does
is hide complexity, which is irrelevant to the problem at hand. 

If we abstract out each layer described above, we can form the following
list:

  - Logic gates abstract away the details of MOSFET and CMOS
  - Machine language abstracts away the details of logic gates
  - Assembly language abstracts away the details of machine languages
  - Programming languages abstracts away the details of assembly languages

And all that is happening here is that we notice there are repeating 
patterns in each layer, which we can utilise to build an upper-layer, 
hiding the complexity of the underlying implementation, making development
simpler. 

Our result, programmers spend more time programming and less time 
writing the same code/instruction/bit over and over again. 