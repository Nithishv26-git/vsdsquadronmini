# VSDsquadron_intern
The program is about the development of RISC-V architecture using the VSD squadron mini board.
# VSD squadron mini board
![1719301997596](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/e3845873-2e6f-47ff-82f7-6331eb2ef3b6)
# Features 
>32-bit RISC-V core based on RV32EC instruction set, optimized for high-performance computing with support for 2-level interrupt nesting.
>Includes a built-in factory-trimmed 24MHz RC oscillator and a 128kHz RC oscillator, plus an external 24MHz oscillator.
>3 groups of GPIO ports, totalling 15 I/O ports.
>2KB SRAM for volatile data storage, 16KB CodeFlash for program memory, and additional 1920B for bootloader functionalities.
<details>
<summary>TASK 1</summary>
<br>
  
# Writing a C code to count sum of numbers from 1 to n using gedit or Leafpad.
  
![Screenshot (195)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/36ba135b-b4a4-47ad-86ed-66e3c598559c)
### Output for the above code:
![Screenshot (196)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/b809ac50-06e3-4bb3-b054-e7d9f7839ac6)
### Compiling the same code for RISC-V:
![Screenshot (197)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/0e7d51be-0a95-4816-816f-1c50518e327e)
</details>

<details>
<summary>TASK 2</summary>
 <br>

# Writing a simple C program for smart elevator controller:

The smart elevator controller is designed to control the basic elevator operations including floor requests,movement and stopping at requested floors.

*The C code for the elevator controller

```#include <stdio.h>
#include <stdlib.h>

#define NUM_FLOORS 10 // Number of floors in the building

// Function prototypes
void moveElevator(int currentFloor, int destinationFloor);
void processRequest(int requestedFloor);

// Global variables
int elevatorCurrentFloor = 0; // Starting floor of the elevator
int main() {
    int requestedFloor;
    while (1) { // Infinite loop for continuous operation
        printf("\nEnter the floor number to request the elevator (0-%d, or -1 to exit): ", NUM_FLOORS - 1);
        scanf("%d", &requestedFloor);

        if (requestedFloor == -1) {
            printf("Exiting elevator control program.\n");
            break;

# Writing a simple C program for smart elevator controller:

The smart elevator controller is designed to control the basic elevator operations including floor requests,movement and stopping at requested floors.

*The C code for the elevator controller

```#include <stdio.h>
#include <stdlib.h>

#define NUM_FLOORS 10 // Number of floors in the building

// Function prototypes
void moveElevator(int currentFloor, int destinationFloor);
void processRequest(int requestedFloor);

// Global variables
int elevatorCurrentFloor = 0; // Starting floor of the elevator
int main() {
    int requestedFloor;
    while (1) { // Infinite loop for continuous operation
        printf("\nEnter the floor number to request the elevator (0-%d, or -1 to exit): ", NUM_FLOORS - 1);
        scanf("%d", &requestedFloor);

        if (requestedFloor == -1) {
            printf("Exiting elevator control program.\n");
            break;
        }

        if (requestedFloor < 0 || requestedFloor >= NUM_FLOORS) {
            printf("Invalid floor number. Please enter a number between 0 and %d.\n", NUM_FLOORS - 1);
            continue;
        }
 processRequest(requestedFloor);
    }

    return 0;
}

void moveElevator(int currentFloor, int destinationFloor) {
    if (currentFloor < destinationFloor) {
        printf("Elevator moving up from floor %d to floor %d.\n", currentFloor, destinationFloor);
    } else if (currentFloor > destinationFloor) {
        printf("Elevator moving down from floor %d to floor %d.\n", currentFloor, destinationFloor);
    } else {
        printf("Elevator is already on floor %d.\n", currentFloor);
    }

    elevatorCurrentFloor = destinationFloor;
}

void processRequest(int requestedFloor) {
    printf("Request received for floor %d.\n", requestedFloor);

    if (requestedFloor == elevatorCurrentFloor) {
        printf("Elevator is already on floor %d. Doors opening.\n", elevatorCurrentFloor);
    } else {
        moveElevator(elevatorCurrentFloor, requestedFloor);
        printf("Doors opening on floor %d.\n", requestedFloor);
    }

    // Additional logic can be added here for handling door operations, etc.
}
```
### compiling the above code using gcc compiler
![Screenshot (17)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/55d36bae-f5f5-4194-8964-47feae513126)

![Screenshot (18)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/42b6482c-69cc-47ef-ac1d-fb4dfcd65980)

![Screenshot (19)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/a657abcf-18d8-48d5-b29c-48e82fdaed9d)

# Functions of this elevator:
This program provides a basic simulation of a smart elevator controller where elevators respond to user requests to move between floors efficiently. In a real-world scenario, additional features such as prioritization of requests, handling multiple requests simultaneously, and fault tolerance would need to be implemented for robust operation.

# OUTPUT of the C code is shown below:

![Screenshot (15)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/781d0033-bd30-4e5b-a176-b8bc02d9cdd8)
# OUTPUT EXPLAINATION:
- 1.At initial condition the elevator is at floor '0':
  Request received for floor '8' ,hence the elevator is moving from floor 0 to 8;
- 2.Now the elevator is at 8th floor :
- Request received for 7th floor ,so the elevator is moving from floor 8 to floor 7;
# Compiling the same program in the RISC-V Simulator:
*prompt for the risc compiler
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -o filename.o filename.c
```
# Finding the assembly code for the RISC-V simulation
Therefore Subtracting the last memory address of the main function from the fisrt memory address of the function next to the main function
![Screenshot (20)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/ca63ca37-15bd-4282-af58-1fab7236450d)
# Finding the number of Instruction sets:

![Screenshot (22)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/29966218-f150-4b04-9f97-d30de10847fe)
# End of task 2
</details>
<details>
<summary>TASK 3</summary>
 <br>


# Simulation of SPIKE and verification with O1 and Ofast command along with the RISC-V.
# >The first step is to run the simple c program which is created using openAI(chatGPT) using the RISC-V commands (i.e)
```
riscv64-unknown-elf-gcc -O1 -mabi=lpv64 -march=rv64i -o (filename)elevatorctrl.o elevatorctrl.c.
```
Execute the program asual by using the commands
```gcc elevatorctrl.c```
and 
```
./a.out
```
Now executing the spike simulation with the help of spike simulation commands 
```
spike pk elevatorctrl.o
```

![Screenshot (24)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/d0b98188-71e1-4f69-bcee-2b79e1ef1fb0)
# Now Finding the number of instructions using the assembly code of the RISC-V with the help of main function
![Screenshot (25)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/02044dfa-61de-4dac-a67c-e6dfda9b7f94)
From the execution of program with and without spike simulation we should get the same output.
# Debugging using the assembly code of the risc-v simulator
*The debugging is done with the help of commands such as 
```
spike -d pk elevatorctrl
```
This command debugs the assembly code by accessing the registers.
The file location is initiated by the command 
```
until pc 0 (starting address)100b0
```
then press Enter and again enter the command reg 0 sp(stack pointer)
![Screenshot (28)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/f6db02f7-e485-45c9-81eb-ce6edc062dea)
# Thus the spike simulation is done by debugging the assembly code of RISC-V
![Screenshot (27)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/07d9013b-7a89-4ae4-8805-0eadbf61cba5)

</details>

<details>
 <summary>TASK 4</summary>
 <br>


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

</details>

<details>
 <summary>TASK 5</summary>
 <br>

# FUNCTIONAL VERIFICATION USING VERILOG AND TESTBENCH CODE:
## To run this simulation there are two tools need to be installed
### 1.iverilog
- Icarus Verilog is an open-source Verilog simulation and synthesis tool. It is used primarily for verifying and testing digital designs written in the Verilog hardware description language (HDL).
- Icarus Verilog can compile and simulate Verilog HDL code, making it a useful tool for verifying the correctness of digital designs.
### 2.GTKWave
- GTKWave is an open-source waveform viewer for viewing the signal changes over time in digital circuits. It is often used in conjunction with simulation tools like Icarus Verilog
- GTKWave provides a graphical interface to view waveform data, making it easier to analyze the behavior of digital circuits.
- Together, Icarus Verilog and GTKWave form a powerful combination for designing, simulating, and analyzing digital circuits using Verilog HDL.
- ## Ubuntu
   - 1.Open your terminal and run this code
```
sudo apt-get update
sudo apt-get install iverilog
```
## Installation of iverilog on ubuntu:

![Screenshot (33)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/bcddde7f-824d-4c13-88c2-339b92f445a8)
### Create a directory under your name,use the command as `mkdir <name> (mkdir filename)`
- To create a two different files in that particular directory use the touch command `touch nithish_v_26.v` and touch `nithish_v26_tb.v`.
- Import the verilog netlist and testbench code into that two files which we have created.
# GTKWave
- GTKwave is an open-source waveform simulator also available in ubuntu softwares,it is used for viewing the signal changes over time in digital circuits.It is often used in conjuction with simulation tools like Icarus Verilog.
  ### Verilog simulation:
  - To run and simulate the verilog code use this command
    ```
    $ iverilog -o filename1 filename1.v filename2.v
    $ ./filename1.v
    ```
  ![Screenshot (37)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/da01226d-0d9b-4bf8-a5c4-2fb1a7a7ad14)
  ### GTKWave:
- For the simulating the waveform in the GTKWave , used this command.
  ```
  gtkwave filename1.vcd
  ```
  ```
  gtkwave nithish_v26.vcd
  ```
  ![Screenshot (36)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/04dcfff0-28e8-46f3-83f7-f182008a39f8)
    
- By observing the Output Waveform of various instructions that we have covered.
- Here we use GTKwave to see the variation at the output.
- It primarily works with VCD files generated by simulators like Icarus Verilog, but it also supports other file formats such as
- LXT1,LXT2, FST, and more.Users can easily navigate through the signals, zoom in and out, and focus on specific areas of interest.
</details>

<details>
 <summary>TASK 6</summary>
 <br>

# ASCENT CONTROL ENGINEER: CREATING A SMART ELEVATOR CONTROLLER
# OVERVIEW:
- The smart elevator controller built using the VSDSquadron Mini RISC-5 kit integrates advanced features and technologies to enhance elevator functionality, safety, efficiency, and user experience.
# Components Required:
- ### VSDSquadron Mini ###
- This serves as the core processing unit based on the RISC-V architecture, providing computational power and interfacing capabilities.
- ### Sensors
-  Position sensors (like encoders), load sensors, and door sensors to monitor elevator status and conditions.
- ### Actuators
-  Motors and relays for controlling elevator movement and door operations.
- ### User Interface Components
-  Display panels, buttons.
-  Breadboard
-  jumper Wires
## Working
- #### Floor Selection:
-  Passengers typically interact with the elevator through a user interface located either inside or outside the elevator car.
- This interface can be a touchscreen, keypad, or button panel.
- ##### Destination Input:
- Passengers select their desired floor using the interface. Some smart elevators may also allow users to input additional parameters, such as whether they are in a rush or have specific accessibility needs.
# Code for smart elevator controller
```
#include <stdint.h>
#include <stdbool.h>

// Define memory-mapped addresses for GPIO control
#define GPIO_BASE_ADDR      0x10000000
#define GPIO_OUTPUT_REG     (*(volatile uint32_t *)(GPIO_BASE_ADDR + 0x00))
#define GPIO_DIRECTION_REG  (*(volatile uint32_t *)(GPIO_BASE_ADDR + 0x04))

// Define GPIO pin assignments for stepper motor control
#define STEP_PIN            0
#define DIR_PIN             1

// Define GPIO pin assignments for LCD control (example)
#define LCD_RS_PIN          2
#define LCD_EN_PIN          3
#define LCD_D4_PIN          4
#define LCD_D5_PIN          5
#define LCD_D6_PIN          6
#define LCD_D7_PIN          7

// Define constants for motor control
#define STEPS_PER_REV       200   // Number of steps per revolution for the stepper motor

// Define elevator floors
#define FLOOR_1             0
#define FLOOR_2             1
#define FLOOR_3             2

// Global variables
volatile uint8_t currentFloor = FLOOR_1;

// Function prototypes
void initGPIO(void);
void moveStepperMotor(uint8_t targetFloor);
void delay(uint32_t milliseconds);  // Function to implement delay

int main(void) {
    initGPIO();

    // Example: Move elevator from floor 1 to floor 3
    moveStepperMotor(FLOOR_3);

    while (1) {
        // Main program loop
    }

    return 0;
}

void initGPIO(void) {
    // Configure GPIO direction (output for stepper motor control)
    GPIO_DIRECTION_REG |= (1 << STEP_PIN) | (1 << DIR_PIN);

    // Configure GPIO direction (output for LCD control - example)
    GPIO_DIRECTION_REG |= (1 << LCD_RS_PIN) | (1 << LCD_EN_PIN) |
                          (1 << LCD_D4_PIN) | (1 << LCD_D5_PIN) |
                          (1 << LCD_D6_PIN) | (1 << LCD_D7_PIN);
}

void moveStepperMotor(uint8_t targetFloor) {
    // Calculate steps needed to move to the target floor
    int8_t stepsToMove = (int8_t)(targetFloor - currentFloor) * (STEPS_PER_REV / 3);

    // Determine direction
    bool direction = (stepsToMove >= 0) ? 1 : 0;
    stepsToMove = abs(stepsToMove);

    // Set direction pin
    if (direction) {
        GPIO_OUTPUT_REG |= (1 << DIR_PIN);  // Set direction pin high for one direction
    } else {
        GPIO_OUTPUT_REG &= ~(1 << DIR_PIN); // Set direction pin low for opposite direction
    }

    // Perform steps
    for (int i = 0; i < stepsToMove; ++i) {
        GPIO_OUTPUT_REG |= (1 << STEP_PIN);  // Pulse step pin
        delay(1);  // Small delay between steps
        GPIO_OUTPUT_REG &= ~(1 << STEP_PIN);
        delay(1);  // Small delay between steps
    }

    // Update current floor
    currentFloor = targetFloor;
}

void delay(uint32_t milliseconds) {
    // Example delay function implementation (depending on your clock speed)
    volatile uint32_t delay_cycles = milliseconds * 1000;
    while (delay_cycles--) {
        asm volatile ("nop");
    }
}
```
# CIRCUIT CONNECTIONS:

![Screenshot (41)](https://github.com/Nithishv26-git/vsdsquadronmini/assets/173581404/6ab01378-37a2-4fe5-9c57-91169de6fb6c)

## Stepper Motor
- Coil1 is connected to the motor driver's 1Y terminal.
- Coil2 is connected to the motor driver's 2Y terminal.
- Coil3 is connected to the motor driver's 3Y terminal.
- Coil4 is connected to the motor driver's 4Y terminal.
## Motor Driver
- VDD (power supply) is connected to the MCU's VIN.
- STEP is connected to a pin (not specified which pin exactly, but it would be a GPIO pin on the MCU).
- DIRECTION is connected to another GPIO pin on the MCU.
- GND is connected to the MCU's GND.
## Proximity Sensor
- VIN is connected to the MCU's VIN.
- OUT is connected to the MCU's PC0 (a GPIO pin).
- GND is connected to the MCU's GND.
## MCU (Microcontroller Unit)
- VIN is connected to the power supply (typically 5V or 3.3V depending on the MCU specifications).
- PDO, PD1 are not connected in the given diagram.
- GND is connected to the common ground.
- PC0 is connected to the proximity sensor's OUT.
- PC1, PC2, PC3 are GPIO pins that could be used for additional connections if needed.
## LCD Display
- VCC is connected to the MCU's VIN (power supply).
- GND is connected to the MCU's GND.
- E (Enable) is connected to a GPIO pin on the MCU.
- RS (Register Select) is connected to another GPIO pin on the MCU.
- D3, D6, D7 are data pins connected to respective GPIO pins on the MCU for sending data to the display.
### Working
The stepper motor is controlled via a motor driver, which receives direction and step signals from the MCU.
The proximity sensor detects objects and sends an output signal to the MCU.
The LCD display shows data and receives control signals from the MCU.
All components share a common ground and power supply (VIN and GND).
These connections allow the MCU to control the stepper motor based on inputs from the proximity sensor and display information on the LCD.

</details>

<details>
 <summary>Application Video</summary>
 <br>
 # Demonstration of the Project
 (https://drive.google.com/file/d/1EjFtfvYl9bJ4m1Ex9OB9L6hJdMUio0fR/view?usp=drivesdk)
  </details>
  
 <details>
*<summary><h4>Acknowledgment</h4></summary>*

>
>I would like to express my special thanking to my mentor *Kunal Ghosh*, and sincere gratitude to *Vlsi System Design* for providing me with the opportunity to intern remotely with their team. This internship has been an invaluable experience, allowing me to delve deep into embedded systems, RISC-V architecture, and VLSI design under the guidance of dedicated mentors.
>
>I am thankful for the support and knowledge imparted to me during this journey. It has significantly enhanced my technical skills and prepared me for future challenges in the field of digital design. I look forward to applying the lessons learned here in my continued pursuit of excellence in engineering.
>
</details>
