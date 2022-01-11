# CPE 315 
## ARM Thumb Simulator

In this project you will build an ARM Thumb simulator to examine performance 
metrics of a given program. You are provided the support code for the 
simulator; you will complete the simulator and collect statistics with it.  This project is broken up into several “milestones”.  The details and requirements for each of the milestones will be supplied by the instructor.

## Tasks
When complete, the simulator will handle a subset of the ARM Thumb instruction set. The following 
list of instructions will be implemented.

  * push
  * pop
  * sub (sp minus immediate)
  * sub (immediate)
  * sub (register)
  * add (sp plus register)
  * add (sp plus immediate)
  * add (register)
  * add (immediate)
  * cmp (register)
  * cmp (immediate)
  * mov (immediate)
  * mov (register)
  * str
  * strb
  * stmia
  * ldr
  * ldrb
  * ldr (literal)
  * ldmia
  * b (unconditional)
  * bcc
  * bcs
  * beq
  * bge
  * bhi
  * ble
  * bls
  * blt
  * bne
  * bl
  * lsl (immediate)
  
The byte memory operations are particularly tricky. The C++ implementation of 
the simulator only reads and writes memory on a word granularity (4 bytes at a 
time), so make sure you work within that constraint.

## Compiling ARM Thumb Test Programs
This process is rather involved, and involves the use of a Raspberry Pi. For 
now, use the provided files. When you need to generate your own test cases, 
 I will post detailed instructions on how to create the simulator input files.

## The Simulator
You get five source files (plus a header file). You should have to only 
modify three of them. Here is what they are and what you should do:

 - [ ] **decode.cpp** associates opcodes with their string equivalents, and 
 prints them if the flags are set. You will need to modify this file to 
 decode the new instructions you encounter. The purpose of decode is to print 
 instructions and to return the correct instruction types to the execute 
 function.
 - [ ] **execute.cpp** is the major file you should change. The simulator 
 calls execute() for each iteration representing an instruction, fetches the 
 current instruction, decodes and evaluates that instruction, changing the 
 machine state (the data memory dmem, the register file rf, and the program 
 counter pc). I have left a few instructions as examples in this file, 
 including some of the trickiest ones to implement. You need to fill in the 
 rest of the instructions and also capture all necessary statistics. 
 - [x] **main.cpp** contains the main routine and parses command-line 
 arguments which may be helpful in debugging:
  * -p dumps the parsed program at the start of the simulation.
  * -d dumps the contents of data memory (all non-zero data memory entries) and the register file after the end of the simulation.
  * -i prints every instruction as it executes.
  * -w prints every write to data memory.
  * -s prints statistics at the end of the program.
  * -c # (fill in # with a size in bytes) enables caches of size #. For this assignment, -c 256 is probably most appropriate.
  * -f simfilename runs the sim file specified. This option must be specified.
    You should not have to change this file.
 - [x] **parse.cpp** parses the sim file. You shouldn't need to change it.
 - [ ] **thumbsim\_driver.cpp** (and thumbsim.hpp) contain the core data 
  structures. You should only need to change one routine in this file, 
  Cache::access, which currently returns a cache miss (false) for every cache 
  access. You will need to enter tags into the cache ("entries") on a miss 
  and check tags on every access.

If you call "thumbsim -c 256" the system automatically instantiates several 
  caches: 256B, 4-byte cache lines; 256B, 8-byte cache lines, etc. 
  (up to 256B, 256-byte cache lines).  The implementation of the cache access routine
  will be completed in one of the milestones.

  Start by typing 'make' to create the thumbsim executable.
  
