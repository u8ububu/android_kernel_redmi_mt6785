MTK_PLATFORM := $(subst ",,$(CONFIG_MTK_PLATFORM))

ifneq ($(LINUX_KERNEL_VERSION),)
CONFIG_KERVER_VERSION := $(word 2,$(subst -, ,$(LINUX_KERNEL_VERSION)))
endif

ifeq ($(CONFIG_KERVER_VERSION),)
$(error CONFIG_KERVER_VERSION is not defined)
endif

MET_ROOT_DIR := $(srctree)/../vendor/mediatek/kernel_modules/met_drv/$(CONFIG_KERVER_VERSION)
MET_COMMON_DIR := $(wildcard $(MET_ROOT_DIR)/common)
MET_PLF_DIR := $(wildcard $(MET_ROOT_DIR)/$(MTK_PLATFORM))
MET_BUILD_DEFAULT := n

ifeq ($(CONFIG_MODULES),y)

ifeq ($(CONFIG_FTRACE),y)
    ifeq ($(CONFIG_TRACING),y)
        FTRACE_READY := y
    endif
endif

$(info ******** Start to build met_drv for $(MTK_PLATFORM) ********)
ifneq ($(MET_PLF_DIR),)
    ifeq ($(FTRACE_READY),y)
        include $(MET_COMMON_DIR)/Kbuild
    else
        $(warning Not building met.ko due to CONFIG_FTRACE/CONFIG_TRACING is not set, build met default)
        MET_BUILD_DEFAULT = y
    endif
else
    $(warning not support $(MTK_PLATFORM), build met default)
    MET_BUILD_DEFAULT = y
endif
else #CONFIG_MODULES = n
    $(warning Not building met.ko due to CONFIG_MODULES is not set, build met default)
    MET_BUILD_DEFAULT := y
endif

ifeq ($(MET_BUILD_DEFAULT),y)
    MET_DEF_DIR := $(MET_ROOT_DIR)/default
    include $(MET_DEF_DIR)/Kbuild
endif
