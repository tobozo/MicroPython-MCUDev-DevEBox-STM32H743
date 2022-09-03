# MicroPython MCUDev DevEBox STM32H743

[MicroPython](https://micropython.org) board support for [MCUDev DevEBox STM32H743](https://stm32-base.org/boards/STM32H743VIT6-STM32H7XX-M).

## Features

This firmware enables these features by default:

+ 8MB exFAT filesystem on [W25Q64JV](https://www.winbond.com/hq/product/code-storage-flash-memory/serial-nor-flash/index.html?__locale=en&partNo=W25Q64JV), Quad SPI.

+ Micropython REPL via USB CDC.

+ UART:
  + UART1: TX/RX on PA9/PA10.
  + UART2: TX/RX on PA2/PA3.

+ I2C:
  + I2C2: SCL/SDA on PB10/PB11.

+ SPI:
  + SPI1: NSS/SCK/MISO/MOSI on PA4/PA5/PA6/PA7.
  + SPI2: NSS/SCK/MISO/MOSI on PB12/PB13/PB14/PB15.

+ CAN:
  + CAN1: TX/RX on PB9/PB8.

+ LED: You can control D2 using pyb.LED(1).

+ SD Card.

+ USB Mass Storage.

## Build

Tested on Ubuntu 22.04.

1. Install dependencies:

   ```bash
   sudo apt update
   sudo apt install -y build-essential git libffi-dev pkg-config gcc-arm-none-eabi binutils-arm-none-eabi libnewlib-arm-none-eabi python3
   ```

2. Check out MicroPython and this repository:

   ```bash
   git clone https://github.com/micropython/micropython.git
   git clone https://github.com/Mythologyli/MicroPython-MCUDev-DevEBox-STM32H743.git
   ```

3. Copy MCUDEV_DEVEBOX_H743 to micropython/ports/stm32/boards:
   
   ```bash
   cp -r MicroPython-MCUDev-DevEBox-STM32H743/MCUDEV_DEVEBOX_H743 micropython/ports/stm32/boards
   ```

4. Build:
   
   ```bash
   cd micropython/ports/stm32
   make submodules
   make BOARD=MCUDEV_DEVEBOX_H743
   ```

## Flash

1. Disconnect USB, connect BT0 to 3V3, then connect USB.

2. Install python3-usb:
   
   ```bash
   sudo apt install -y python3-usb
   ```

3. Flash:
   
   ```bash
   make BOARD=MCUDEV_DEVEBOX_H743 deploy
   ```

*You can use [STM32CubeProgrammer](https://www.st.com/zh/development-tools/stm32cubeprog.html) in Microsoft Windows. The firmware can be found in micropython/ports/stm32/build-MCUDEV_DEVEBOX_H743.*

## Board

![](https://stm32-base.org/assets/img/boards/STM32H743VIT6_STM32H7XX_M-1.jpg)

![](https://stm32-base.org/assets/img/boards/STM32H743VIT6_STM32H7XX_M-2.jpg)

![](https://stm32-base.org/assets/img/boards/STM32H743VIT6_STM32H7XX_M-3.jpg)

More information: [STM32H743VIT6-STM32H7XX-M](https://stm32-base.org/boards/STM32H743VIT6-STM32H7XX-M).

## Reference

+ [mcauser/MCUDEV_DEVEBOX_H7XX_M](https://github.com/mcauser/MCUDEV_DEVEBOX_H7XX_M)
+ [micropython](https://github.com/micropython/micropython)