CROSS-COMPILER = arm-none-eabi-

all: usart.bin

usart.bin: main.c blink.c startup.c vector_table.s
	$(CROSS-COMPILER)gcc -std=c11 -Wall -mcpu=cortex-m4 -mthumb -nostartfiles -T stm32f4.ld main.c blink.c startup.c vector_table.s -o usart.elf
	$(CROSS-COMPILER)objcopy -O binary usart.elf usart.bin

flash:
	st-flash --reset write usart.bin 0x8000000

clean:
	rm -f *.o *.elf *.bin
