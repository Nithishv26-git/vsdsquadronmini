# TASK 6
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

