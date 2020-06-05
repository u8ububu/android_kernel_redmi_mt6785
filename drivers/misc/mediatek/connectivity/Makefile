#
# Copyright (C) 2015 MediaTek Inc.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#

# Connectivity combo driver
# If KERNELRELEASE is defined, we've been invoked from the
# kernel build system and can use its language.

    subdir-ccflags-y += -I$(srctree)/
    subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/include
    subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/include/clkbuf_v1
    subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/base/power/include/clkbuf_v1/$(MTK_PLATFORM)
    subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/include/mt-plat/$(MTK_PLATFORM)/include
    subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/include/mt-plat
ifeq ($(CONFIG_MTK_PMIC_CHIP_MT6359),y)
    subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/pmic/include/mt6359
endif
    subdir-ccflags-y += -I$(srctree)/drivers/mmc/core
    subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/eccci/$(MTK_PLATFORM)
    subdir-ccflags-y += -I$(srctree)/drivers/misc/mediatek/eccci/
    subdir-ccflags-y += -I$(srctree)/drivers/clk/mediatek/
    subdir-ccflags-y += -I$(srctree)/drivers/pinctrl/mediatek/

    # Do Nothing, move to standalone repo
    MODULE_NAME := connadp
    obj-y += $(MODULE_NAME).o
    $(MODULE_NAME)-objs += common/connectivity_build_in_adapter.o
    $(MODULE_NAME)-objs += common/wmt_build_in_adapter.o


    # Do build-in for Makefile checking
    export CONFIG_WLAN_DRV_BUILD_IN=y

#    ifeq ($(CONFIG_WLAN_DRV_BUILD_IN),y)

        # Do build-in for xxx.c checking
        
        export MTK_COMBO_CHIP=$(MTK_COMBO_CHIP_NAME)
        
        subdir-ccflags-y += -D MTK_WCN_BUILT_IN_DRIVER
        subdir-ccflags-y += -D CFG_ENABLE_KEYWORD_EXCEPTION_MECHANISM
        
        obj-y += common/
#        obj-$(MTK_COMBO_WIFI) += wlan/adaptor/
#        obj-$(MTK_WLAN_GEN4M) += wlan/core/gen4m/
#        obj-$(MTK_COMBO_GPS) += gps/
#        obj-$(MTK_FMRADIO) += fmradio/
#        obj-$(MTK_COMBO_BT) += bt/mt66xx/
#        obj-$(MTK_BT_MT76XX) += bt/mt76xx/sdio/
	export CONFIG_MTK_COMBO_WIFI_HIF=axi
	export MTK_COMBO_CHIP=CONNAC
	export WLAN_CHIP_ID=6785
	export MTK_ANDROID_WMT=y
	export WIFI_IP_SET=2
	
        obj-y += wlan/adaptor/
        obj-y += wlan/core/gen4m/
        obj-y += gps/
        obj-n += fmradio/
        obj-y += bt/mt66xx/
        obj-n += bt/mt76xx/sdio/
        

