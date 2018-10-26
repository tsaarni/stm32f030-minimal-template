# Minimal Mbed OS project template for barebones STM32F030

This is a template for a barebones STM32F030F4 project.

The project uses Mbed OS which is not optimized for memory footprint but
very short applications will still fit into 16KB flash of STM32F030F4 after disabling stdio library support.

Alternative printf implementation is included from [here](https://github.com/janjongboom/mbed-coremark-lm32-printf).

The development environment is based on PlatformIO.
It re-uses nucleo_f030r8 as target board, which is based on newlib-nano for smaller binary size.
Board details are overwritten in platformio.ini file.


## Connecting ST-LINK/V2 to STM32F030F4

Minimum connections for flashing are depicted below


                     +------------+
    GND -----> BOOT0 | 1       20 | PA14 <------------- SWCLK
              OSC-IN | 2       19 | PA13 <------------- SWDIO
             OSC-OUT | 3       18 | PA10/USART1_RX
                NRST | 4       17 | PA9/USART1_TX ----> UART RX
    3V3 ----->  VDDA | 5       16 | VDD  <------------- 3V3
                 PA0 | 6       15 | VSS  <------------- GND
                 PA1 | 7       14 | PB1
                 PA2 | 8       13 | PA7
                 PA3 | 9       12 | PA6
                 PA4 | 10      11 | PA5
                     +------------+


## Programming

Compile and flash

    pio run -t upload


View serial debug logs

    pio device monitor -b 115200


## Manuals

* STM32F030x4 [Datasheet](https://www.st.com/resource/en/datasheet/dm00088500.pdf)
* RM0360 Reference Manual [STM32F030x4/x6/x8/xC and STM32F070x6/xB advanced ARM based 32-bit MCUs](https://www.st.com/content/ccc/resource/technical/document/reference_manual/cf/10/a8/c4/29/fb/4c/42/DM00091010.pdf/files/DM00091010.pdf/jcr:content/translations/en.DM00091010.pdf)
  * memory and peripherals (e.g. boot modes)
* AN4325 Application Note [Getting started with STM32F030xx and STM32F070xx series hardware development](https://www.st.com/content/ccc/resource/technical/document/application_note/91/66/2d/8c/f9/b5/47/55/DM00089834.pdf/files/DM00089834.pdf/jcr:content/translations/en.DM00089834.pdf)
* [Mbed OS Documentation](https://os.mbed.com/docs/)
