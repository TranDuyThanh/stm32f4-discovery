# using STM32F4 DISCOVERY with OSX

## Setup
##### Install STLINK

	brew install automake autoconf libusb libusb-compat pkg-config
	sudo easy_install pyyaml

	git clone https://github.com/texane/stlink.git
	cd stlink/
	./autogen.sh
	./configure
	make

##### Install OPENOCD
	
	brew install mpfr gmp libmpc texinfo libusb-compat libftdi wget
	brew install openocd
	
##### Install arm-none-eabi

	brew install https://raw.github.com/PX4/homebrew-px4/master/gcc-arm-none-eabi-48.rb
	sudo easy_install pyyaml
	
##### Debug with OPENOCD
	
	openocd -f board/stm32f4discovery.cfg
	
## Load .elf to stm32f4
	
Type this on the first shell window
	st-util 4242 usb

type this on the second shell
	
	arm-none-eabi-gdb
	target remote :4242
	monitor reset halt
	load file.elf

######Another way

	st-flash write file.bin 0x8000000

# Using STM32F4 DISCOVERY with Ubuntu 14.04

	sudo apt-get remove binutils-arm-none-eabi gcc-arm-none-eabi
	sudo add-apt-repository ppa:terry.guo/gcc-arm-embedded
	sudo apt-get update
	sudo apt-get install gcc-arm-none-eabi=4.9.3.2015q1-0trusty13