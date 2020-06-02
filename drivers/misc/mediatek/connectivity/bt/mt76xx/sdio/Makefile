###############################################################################
# Bluetooth character device driver

###############################################################################
# Necessary Check

ifneq ($(AUTOCONF_H),)
    ccflags-y += -imacros $(AUTOCONF_H)
endif

MODULE_NAME := btmtksdio
obj-m += $(MODULE_NAME).o

#ccflags-y += -D CREATE_NODE_DYNAMIC=1

$(MODULE_NAME)-objs += btmtk_sdio.o \
                       btmtk_main.o
