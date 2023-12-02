# Sliding dot project

Objectives:
- Connect and configure gyroscope L3GD20 via SPI.
- Connect and set up the LED matrix 32x16 dots via SPI.
- Display the image on the matrix and move it depending on the gyroscope readings.

Microcontroller clocking settings based on STM32F411 Discovery kit:
![Microcontroller clocking settings](https://github.com/chocolateicecreamlover/stm32-lab-1-sliding-dot/assets/152575505/d319d007-1db1-4fe0-bbb2-8470ec8fafd9)

Assignment of microcontroller pins:
![Microcontroller pins setting](https://github.com/chocolateicecreamlover/stm32-lab-1-sliding-dot/assets/152575505/a56bd8fb-ec7c-416c-9a6f-5bf83088bbcc)

Gyroscope L3GD20:
Refers to files L3GD20.c (.h)

All macroses are found on [official stm32 github repo](https://github.com/STMicroelectronics/stm32-l3gd20).
Basic settings:
- Upper and lower measurement limit ± 250 ̊/s.
- Data transmission frequency 760 Hz.
- All built-in filters are enabled, including low- and high-frequency.

HAL library function HAL_SPI_TransmitReceive() is used for data exchange between the microcontroller and the gyroscope. After initialization of the gyroscope before the main program cycle operation it is necessary to read data from it once.

LED matrix:
The matrix works on the principle of dynamic indication and turns on one of four groups of LEDs in turn - only LEDs of a particular group can be on at a time. The data about the switched on LEDs are transferred to the shift registers of the matrix (choosed by pins A, B). The matrix has pins for receiving information via SPI in slave mode. Also the connector of the matrix has a pin to enable the matrix operation and a pin to update the data in the shift registers. The matrix is powered externally.
The algorithm for working with the matrix is described in the [article](https://habr.com/ru/articles/372215/) (in russian).

Matrix connector 
![Matrix connector](https://github.com/chocolateicecreamlover/stm32-lab-1-sliding-dot/assets/152575505/bd10701a-7488-44a5-a4c0-702cde287a92)

## How to use
- Open LB_1_1_Sliding_Dot.ioc with CubeMX
- Export project to IDE of your choice via CubeMX
- Set up all dependencies between files
- Connect the components
- Flash project to STM32F411 Discovery kit
