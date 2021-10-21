obj-m	:= fpga_dip_switch_driver.o

KDIR	:= /root/work/achroimx6q/kernel
PWD	:= $(shell pwd)

all: driver app

driver:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules ARCH=arm
app:
	arm-none-linux-gnueabi-gcc -static -o fpga_test_dip_switch fpga_test_dip_switch.c

install:
	cp -a fpga_dip_switch_driver.ko /nfsroot
	cp -a fpga_test_dip_switch /nfsroot
clean:
	rm -rf *.ko
	rm -rf *.mod.*
	rm -rf *.o
	rm -rf fpga_test_dip_switch
	rm -rf Module.symvers
	rm -rf .tmp*
	rm -rf .fpga*
	rm -rf modules.order
