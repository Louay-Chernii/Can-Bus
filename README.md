#LED Control via CAN Bus Nodes

**Description:**
This project showcases a fundamental implementation of CAN Bus communication between STM32F407G-DISC1 nodes and a central gateway, facilitating control of the internal LEDs on the STM32 boards based on user input.

**Features:**
- Utilizes three STM32F407G-DISC1 development boards.
- User buttons on each node trigger LED updates and transmit data via the CAN Bus.
- The STM32F407G-DISC1 gateway receives LED data and adjusts its own internal LED accordingly.

**Hardware:**
- 3x STM32F407G-DISC1 development boards
- 3x CAN Bus transceivers

**Software:**
- STM32CubeIDE
- C programming language

**Included Files:**
- `main.c`: Contains core application logic for both nodes and gateway.
- `stm32f4xx_hal.h`: STM32 HAL library header.

**Building and Deploying the Project:**
1. Install STM32CubeIDE and configure it for your STM32F407V development boards.
2. Import this project into STM32CubeIDE.
3. For the Gateway: Update the `main.c` file in the `gateway/` folder with any necessary configuration changes (e.g., CAN Bus filtering based on `NODE_ID`).
4. For each Node: Update the `main.c` file in the `node/` folder with the appropriate `BOARD` value (e.g., `#define BOARD 1` for the first node, `#define BOARD 2` for the second, etc.).
5. Build and deploy the code to your respective STM32F407G-DISC1 boards (gateway and each node).

**Hardware Connections:**
- Connect user buttons to designated GPIO pins on the STM32F407V boards configured as interrupts.
- Connect CAN transceivers to the CAN Bus according to their datasheets.

**Understanding the Code:**
The code leverages STM32 HAL libraries to interact with peripherals like GPIO, ADC, and CAN. When a user presses a button on one of the nodes, the code triggers functions that:
1. Read the potentiometer value using the ADC.
2. Convert the potentiometer value to determine the number of LEDs to light.
3. Control the internal LEDs of the node by turning on the appropriate number of LEDs based on the converted value.
4. Use CAN Bus communication functions to transmit this number (representing the lit LEDs) as data to the gateway.
5. The gateway receives the data from the node and adjusts its own internal LEDs to match the number of LEDs indicated by the received data.
