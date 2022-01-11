## ARM Thumb Simulator

This repository contains an ARM Thumb simulator to examine performance 
metrics of a given program. 

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

 - [x] **main.cpp** contains the main routine and parses command-line 
 arguments which may be helpful in debugging:
  * -p dumps the parsed program at the start of the simulation.
  * -d dumps the contents of data memory (all non-zero data memory entries) and the register file after the end of the simulation.
  * -i prints every instruction as it executes.
  * -w prints every write to data memory.
  * -s prints statistics at the end of the program.
  * -c # (fill in # with a size in bytes) enables caches of size #. For this assignment, -c 256 is probably most appropriate.
  * -f simfilename runs the sim file specified. This option must be specified.
 - [x] **parse.cpp** parses the sim file. You shouldn't need to change it.
 - [ ] **thumbsim\_driver.cpp** (and thumbsim.hpp) contain the core data 
  structures.
  
If you call "thumbsim -c 256" the system automatically instantiates several 
  caches: 256B, 4-byte cache lines; 256B, 8-byte cache lines, etc. 
  (up to 256B, 256-byte cache lines).  The implementation of the cache access routine
  will be completed in one of the milestones.

  Start by typing 'make' to create the thumbsim executable.
  
