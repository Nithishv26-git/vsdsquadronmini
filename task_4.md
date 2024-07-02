#TASK 4
# RISC-V Instruction Types and extraction of 32-bit instruction in the instruction type format.
RISC-V instructions can be broadly categorized into six types based on their format and structure:

* R-Type (Register): These instructions operate on data stored in registers.
* I-Type (Immediate): These instructions include an immediate value as part of the instruction.
* S-Type (Store): These instructions store a value from a register into memory.
* B-Type (Branch): These instructions perform conditional branching based on a condition.
* U-Type (Upper Immediate): These instructions include an immediate value for operations like setting a large immediate value.
* J-Type (Jump): These instructions perform unconditional jumps.
# 1. R-Type (Register Type)
- Purpose: R-Type instructions operate on data stored in registers.
- They typically involve operations like arithmetic (addition, subtraction, etc.) and logical operations (AND, OR, XOR).
- Opcode Range: 0x33 (in hexadecimal) or 0110011 (in binary).

Example Instructions:

* "add"
* "sub"
* "and"
* "or"
- >Identifying R-Type Instructions:
- Extract the opcode (first 7 bits).
- Check if the opcode matches 0x33 (in hexadecimal) or 0110011 (in binary).
```
add x1, x2, x3   ; x1 = x2 + x3
```
#  2.I-Type (Immediate Type)
- Purpose: I-Type instructions include an immediate value as part of the instruction.
- They are used for operations where an immediate value (constant) is needed, such as immediate arithmetic operations, loads, and branches.
- Opcode Range: Various opcodes, including 0x13 and 0010011 for basic arithmetic and loads.
- >Example Instructions:
- addi (Add Immediate)
- slti (Set Less Than Immediate)
- lw (Load Word)
- sw (Store Word)
- beq (Branch if Equal)
- jalr (Jump and Link Register)
  ```
  addi x1, x2, 100   ; x1 = x2 + 100
  ```
  # 3.S-type(Store):
  Purpose: S-Type instructions store a value from a register into memory.

- Examples:

- sb: Stores the least-significant byte of a register into memory.
- sh: Stores the least-significant halfword of a register into memory.
- sw: Stores a 32-bit word from a register into memory.
- >Example Code:
```
  sb x1, 8(x2)   ; Store byte from x1 into memory at address x2 + 8
```
# 4.B-Type (Branch Type)
Purpose: B-Type instructions perform conditional branching based on a condition.

- Examples:
- beq: Branches to a target address if two registers are equal.
- bne: Branches to a target address if two registers are not equal.
- blt: Branches to a target address if one register is less than another.
- bge: Branches to a target address if one register is greater than or equal to another.
- >Example Code:
  ```
  beq x1, x2, label1  ; Branch to label1 if x1 equals x2
  ```
  
