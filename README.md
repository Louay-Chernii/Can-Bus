# LED Control via CAN Bus Nodes

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
3. For each Node: Update the `main.c` file in the `node/` folder with the appropriate `BOARD` value (e.g., `#define BOARD 1` for the first node, `#define BOARD 2` for the second, etc.).
4. Build and deploy the code to your respective STM32F407G-DISC1 boards.

**Hardware Connections:**
- Connect user buttons to designated GPIO pins on the STM32F407V boards configured as interrupts.
- Connect CAN transceivers to the CAN Bus according to their datasheets.

**Understanding the Code:**

The code utilizes STM32 HAL libraries to control GPIO and CAN peripherals. Here’s how it works:

***1-Initialization:***

-The system clock, GPIO, and CAN1 are initialized.

-CAN filter settings are configured to accept all messages.

-CAN communication and notifications for incoming messages are activated.

***2-Main Loop:***

-The program waits for the user button press.

-On button press, all LEDs on the board are turned off.

-A CAN message with the board ID is transmitted.

***3-CAN Receive Callback:***

-When a CAN message is received, the callback function processes it.

-If the message ID matches the expected value, the received data determines which LEDs to light up on the board.
