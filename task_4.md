# TASK 4
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
  # 5. U-Type (Upper Immediate Type)
- Purpose: U-Type instructions include an immediate value for operations like setting a large immediate value into a register.

- >Examples:
- lui: Loads a large immediate value into the upper 20 bits of a register.
- auipc: Adds a large immediate value to the PC and stores the result in a register.
- >Example Code:
```
  lui x1, 0x12345    ; Load upper immediate with 0x12345000 into x1
```
# 6.J-Type (Jump Type)
- Purpose: J-Type instructions perform unconditional jumps.

- >Examples:

- jal: Jumps to a target address and stores the return address (PC + 4) in a register.
- >Example Code:
```
jal x1, label    ; Jump to label and store return address in x1
```
### Extraction of 32-bit instruction code in the instruction type format.
#### 1.Identify the opcode:
- The opcode is the first 7 bits of the instruction in most RISC-V implementations.
- instruction = 0x01234567
- opcode = instruction & 0x7F
- >Here, opcode = 0x67.
#### 2.Determine the instruction type:

- Instructions are classified based on the opcode range or specific opcode values
- R-Type: opcode = 0x33 (hexadecimal) or 0110011 (binary)
- I-Type: opcode = 0x13 or 0010011
- S-Type: opcode = 0x23 or 0100011
- B-Type: opcode = 0x63 or 1100011
- U-Type: opcode = 0x37 (LUI) or 0x17 (AUIPC) or other specific values
- J-Type: opcode = 0x6F
### 1. ADD r1, r2, r3
- **Type:** R-Type (Register Type)
- **Instruction:** `add r1, r2, r3`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x033082b3
```
Explanation:
- `add` corresponds to the opcode `0x33`.
- `r1` (rd) corresponds to register 1 (`0x01` in binary).
- `r2` (rs1) corresponds to register 2 (`0x02` in binary).
- `r3` (rs2) corresponds to register 3 (`0x03` in binary).
- >Funct3 = 000, Funct7 = 0000000 (for ADD operation).

### 2. SUB r3, r1, r2
- **Type:** R-Type (Register Type)
- **Instruction:** `sub r3, r1, r2`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x403282b3
```
Explanation:
- `sub` corresponds to the opcode `0x33`.
- `r3` (rd) corresponds to register 3 (`0x03` in binary).
- `r1` (rs1) corresponds to register 1 (`0x01` in binary).
- `r2` (rs2) corresponds to register 2 (`0x02` in binary).
- >Funct3 = 000, Funct7 = 0100000 (for SUB operation).

### 3. AND r2, r1, r3
- **Type:** R-Type (Register Type)
- **Instruction:** `and r2, r1, r3`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x00308233
```
Explanation:
- `and` corresponds to the opcode `0x33`.
- `r2` (rd) corresponds to register 2 (`0x02` in binary).
- `r1` (rs1) corresponds to register 1 (`0x01` in binary).
- `r3` (rs2) corresponds to register 3 (`0x03` in binary).
- >Funct3 = 111, Funct7 = 0000000 (for AND operation).

### 4. OR r8, r2, r5
- **Type:** R-Type (Register Type)
- **Instruction:** `or r8, r2, r5`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x0050a233
```
Explanation:
- `or` corresponds to the opcode `0x33`.
- `r8` (rd) corresponds to register 8 (`0x08` in binary).
- `r2` (rs1) corresponds to register 2 (`0x02` in binary).
- `r5` (rs2) corresponds to register 5 (`0x05` in binary).
- >Funct3 = 110, Funct7 = 0000000 (for OR operation).

### 5. XOR r8, r1, r4
- **Type:** R-Type (Register Type)
- **Instruction:** `xor r8, r1, r4`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x4060a233
```
Explanation:
- `xor` corresponds to the opcode `0x33`.
- `r8` (rd) corresponds to register 8 (`0x08` in binary).
- `r1` (rs1) corresponds to register 1 (`0x01` in binary).
- `r4` (rs2) corresponds to register 4 (`0x04` in binary).
- >Funct3 = 100, Funct7 = 0100000 (for XOR operation).

### 6. SLT r10, r2, r4
- **Type:** R-Type (Register Type)
- **Instruction:** `slt r10, r2, r4`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x4090a033
```
Explanation:
- `slt` corresponds to the opcode `0x33`.
- `r10` (rd) corresponds to register 10 (`0x0A` in binary).
- `r2` (rs1) corresponds to register 2 (`0x02` in binary).
- `r4` (rs2) corresponds to register 4 (`0x04` in binary).
- >Funct3 = 010, Funct7 = 0000000 (for SLT operation).

### 7. ADDI r12, r3, 5
- **Type:** I-Type (Immediate Type)
- **Instruction:** `addi r12, r3, 5`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x00519013
```
Explanation:
- `addi` corresponds to the opcode `0x13`.
- `r12` (rd) corresponds to register 12 (`0x0C` in binary).
- `r3` (rs1) corresponds to register 3 (`0x03` in binary).
- Immediate value 5 is represented as `0x005` in hexadecimal.
- >Funct3 = 000.

### 8. SW r3, r1, 4
- **Type:** S-Type (Store Type)
- **Instruction:** `sw r3, r1, 4`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x00410223
```
Explanation:
- `sw` corresponds to the opcode `0x23`.
- `r3` (rs2) corresponds to register 3 (`0x03` in binary).
- `r1` (rs1) corresponds to register 1 (`0x01` in binary).
- Immediate offset 4 is represented as `0x004` in hexadecimal.
- >Funct3 = 010.

### 9. SRL r16, r11, r2
- **Type:** R-Type (Register Type)
- **Instruction:** `srl r16, r11, r2`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x0022b053
```
Explanation:
- `srl` corresponds to the opcode `0x33`.
- `r16` (rd) corresponds to register 16 (`0x10` in binary).
- `r11` (rs1) corresponds to register 11 (`0x0B` in binary).
- `r2` (rs2) corresponds to register 2 (`0x02` in binary).
- >Funct3 = 101, Funct7 = 0000000 (for SRL operation).

### 10. BNE r0, r1, 20
- **Type:** B-Type (Branch Type)
- **Instruction:** `bne r0, r1, 20`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x01500063
```
Explanation:
- `bne` corresponds to the opcode `0x63`.
- `r0` (rs1) corresponds to register 0 (`0x00` in binary).
- `r1` (rs2) corresponds to register 1 (`0x01` in binary).
- Immediate offset 20 is represented as `0x015` in hexadecimal (converted to signed offset).
- >Funct3 = 001.

### 11. BEQ r0, r0, 15
- **Type:** B-Type (Branch Type)
- **Instruction:** `beq r0, r0, 15`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x00f00063
```
Explanation:
- `beq` corresponds to the opcode `0x63`.
- Both `r0` (rs1) and `r0` (rs2) correspond to register 0 (`0x00` in binary).
- Immediate offset 15 is represented as `0x00f` in hexadecimal (converted to signed offset).
- Funct3 = 000.

### 12. LW r13, r11, 2
- **Type:** I-Type (Immediate Type)
- **Instruction:** `lw r13, r11, 2`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x00259303
```
Explanation:
- `lw` corresponds to the opcode `0x03`.
- `r13` (rd) corresponds to register 13 (`0x0D` in binary).
- `r11` (rs1) corresponds to register 11 (`0x0B` in binary).
- Immediate offset 2 is represented as `0x002` in hexadecimal.
- >Funct3 = 010.

### 13. SLL r15, r11, r2
- **Type:** R-Type (Register Type)
- **Instruction:** `sll r15, r11, r2`

**Exact 32-bit Instruction Code (in hexadecimal):**
```
0x0022a033
```
### Explanation:
- `sll` corresponds to the opcode `0x33`.
- `r15` (rd) corresponds to register 15 (`0x0F` in binary).
- `r11` (rs1) corresponds to register 11 (`0x0B` in binary).
- `r2` (rs2) corresponds to register 2 (`0x02` in binary).
- >Funct3 = 001, Funct7 = 0000000 (for SLL operation).

- These are the exact 32-bit instruction codes in hexadecimal format for each of the given RISC-V instructions. Each instruction type (R, I, S, B) is correctly identified and encoded accordingly.
