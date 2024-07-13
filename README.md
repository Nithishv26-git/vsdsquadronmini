# VSDsquadron_intern
The program is about the development pf RISC-V architecture using the VSD squadron mini board.
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
