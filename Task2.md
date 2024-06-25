# Task 2
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
}```
