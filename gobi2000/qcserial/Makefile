obj-m += qcserial.o

KDIR := /lib/modules/$(shell uname -r)
PWD  := $(shell pwd)

all: default

default:
	$(MAKE) -C $(KDIR)/build SUBDIRS=$(PWD) modules

clean:
	$(MAKE) -C $(KDIR)/build SUBDIRS=$(PWD) clean
	@rm -f modules.order
	@rm -f Module.markers
	@rm -f *~

install:
	cp qcserial.ko $(KDIR)/kernel/drivers/usb/serial/
	depmod -a

uninstall:
	rm $(KDIR)/kernel/drivers/usb/serial/qcserial.ko
	rmmod qcserial
