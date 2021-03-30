SUBDIRS=wpa_supplicant
include ../../../../include/MakeConfig

SYSTEM_DIR = ../../../..
all:
	$(MAKE) -C $(SUBDIRS) 

clean:
	for d in $(SUBDIRS); do [ -d $$d ] && $(MAKE) -C $$d clean; done
	rm -f *~

install:
	for d in $(SUBDIRS); do [ -d $$d ] && $(MAKE) -C $$d install; done
