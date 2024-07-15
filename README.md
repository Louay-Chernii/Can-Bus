# Can-Bus
LED control system using user buttons across three STM32F407VG boards, communicating via the CAN (Controller Area Network) protocol. When the user presses a button, a CAN frame is sent across the network, and each STM32F407VG board interprets the received message to adjust the state of the LEDs accordingly.
