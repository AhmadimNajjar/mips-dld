# mips-dld
MIPS Single-Cycle Datapath With Control.

Simulated using Logisim.

-------------
Instructions that work on our implementation:

1. And (and)
2. Or (or)
3. Add (add)
4. Subtract (sub)
5. Load Word (lw)*
6. Store Word (sw)*
7. Branch On Equal (beq)*
8. Jump (j)*


-------------
Please note a few things:

1. To simplify the circuit, we used a 24-bit memory, with each location storing a word.
   So, sw and lw instructions will read their word from one adress only (instead of
   reading 4 bytes from 4 consecutive locations), which means we will be using only
   the first 24 bits from our addresses.
   This also affects our PC and instruction memory, but since our PC is always a multiple
   of 4, we can make it a 26 bit register and use only the last 24 bits (the first 2 bits
   are always 0), so in the beq instruction we will only be using the first 26 bits of the
   shifted sign-extended immediate, but the jump instruction will not need concatenation
   because the address field is long enough to reach all the PC range (all the instruction
   memory). 

2. We did not implement some instructions like Set Less Than (slt) because they were not 
   included in the control unit that we studied in the slides.

3. All the registers are accessable and can be written on (for simple debugging and testing),
   but the $zero register is set to always be 0.

4. To test our implementation, we have included "Test.txt".
