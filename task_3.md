# TASK 3
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
