TO COMPILE AND LOAD THIS CODE:

Point your command prompt to this directory and run each line separately:

arm-none-eabi-as -mcpu=cortex-m0 -mthumb -mapcs-32 -gstabs -ahls=main.lst -o main.o main.s

arm-none-eabi-ld -v -T stm32f1_new.ld -nostartfiles -o pattern-flasher.elf main.o

arm-none-eabi-objcopy -O binary pattern-flasher.elf  pattern-flasher.bin

arm-none-eabi-gdb pattern-flasher.elf

target remote localhost:3333

monitor reset halt

load

continue

>> PROFIT!

NB: This uses an incorrect (but functional) linker script intended for the STM32F1. To be fixed soon!


Old notes:


meaning: http://www.kunen.org/uC/gnu_tool.html
instruction set: http://www.ic.unicamp.br/~ranido/mc404/arm/arm-instructionset.pdf
more about instruction set: http://simplemachines.it/doc/arm_inst.pdf
video on gdb for a snake game: http://hackaday.com/2012/09/27/beginners-look-at-on-chip-debugging/

arm-none-eabi-as -mcpu=cortex-m1 -mthumb -mapcs-32 -gstabs -ahls=led_stm32.lst -o led_stm32.o led_stm32.asm

arm-none-eabi-ld -v -T stm32f1_new.ld -nostartfiles -o led-stm32.elf led-stm32.o

arm-none-eabi-objcopy -O binary led-stm32.elf  led-stm32.bin


#use the -T flag to negate the need for a linker file!
arm-none-eabi-ld -Ttext=0x0 -o add.elf add.o


