# Bootloader_Application


Tools Used:

STM32CubeMX: STM32CubeMX is a graphical software configuration tool that allows you to generate initialization code for STM32 microcontrollers. It simplifies the setup of the microcontroller and its peripherals.
Keil uVision 5: Keil uVision is an integrated development environment (IDE) for developing software for microcontrollers, including the STM32 series.

Functionalities:

UART Communication Protocol: The bootloader project implements a UART communication protocol to communicate with a host computer. The host is controlled by a Python script that supervises the entire process.
CRC Algorithm for Error Handling: To ensure data integrity, the project employs a CRC (Cyclic Redundancy Check) algorithm for error handling. The CRC is computed and checked to verify data integrity during communication.

Features:

Get Version of Bootloader Command: This command allows the host to query the bootloader for its version information.
Get Help Command: The "get help" command provides information about available commands and their usage.
Get Chip ID: This command retrieves the unique identifier of the STM32F103C8 chip.
Get Read Protection Status of Chip: It enables the host to check whether read protection is enabled on the chip.
Go To Address Command: This command instructs the bootloader to jump to a specific address, typically the address of the application in flash memory, to start its execution.
Flash Erase Command: The "flash erase" command is used to erase flash memory pages. It typically takes the page number to erase and the number of pages to erase.
Memory Write Command: This command is responsible for writing application binary data to the flash memory. It requires the starting address for writing and the host sends the binary data for the bootloader to write to the flash.

Mechanism:

Host Control: The host computer, running a Python script, controls the entire bootloader process. It sends commands to the bootloader via UART communication.
CRC Check: To ensure data integrity, the host calculates CRC values for the data it sends to the bootloader. The bootloader also computes CRC values and compares them with the received CRC values to confirm data correctness.

Main Commands:

Flash Erase Command: The host sends the page number and the number of pages to erase. The bootloader performs the flash erase operation as instructed.
Memory Write Command: The host sends the starting address for writing, and then it sends the application binary data. The bootloader writes this data to the flash memory.
Go To Address Command: The host specifies the address where the bootloader should jump to execute the application code. Typically, this is the start address of the application in flash memory.

Overall, this bootloader project provides a means for updating and managing the firmware on an STM32F103C8 microcontroller, offering essential features like flash erase, memory write, and secure communication with error-checking through CRC. It allows for efficient and reliable firmware updates and execution control.
