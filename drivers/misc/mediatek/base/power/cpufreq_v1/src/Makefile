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

ccflags-y += -DMET_USER_EVENT_SUPPORT

ifeq ($(CONFIG_BUILD_ARM64_APPENDED_DTB_IMAGE_NAMES),"mediatek/mt6885_3gear")
ccflags-y += -I$(CPUFREQ_ROOT_DIR)/src/mach/mt6893
include $(srctree)/drivers/misc/mediatek/base/power/cpufreq_v1/src/mach/mt6893/Makefile
else
ifeq ($(CONFIG_MACH_MT6893),y)
ccflags-y += -I$(CPUFREQ_ROOT_DIR)/src/mach/mt6893
include $(srctree)/drivers/misc/mediatek/base/power/cpufreq_v1/src/mach/mt6893/Makefile
else
ifeq ($(CONFIG_MACH_MT6833),y)
ccflags-y += -I$(CPUFREQ_ROOT_DIR)/src/mach/mt6833
include $(srctree)/drivers/misc/mediatek/base/power/cpufreq_v1/src/mach/mt6833/Makefile
else
ifeq ($(CONFIG_MACH_MT6877),y)
ccflags-y += -I$(CPUFREQ_ROOT_DIR)/src/mach/mt6877
include $(srctree)/drivers/misc/mediatek/base/power/cpufreq_v1/src/mach/mt6877/Makefile
else
ifeq ($(CONFIG_MACH_MT6781),y)
ccflags-y += -I$(CPUFREQ_ROOT_DIR)/src/mach/mt6781
include $(srctree)/drivers/misc/mediatek/base/power/cpufreq_v1/src/mach/mt6781/Makefile
else
ifdef CONFIG_MTK_PLATFORM
MTK_PLATFORM := $(subst ",,$(CONFIG_MTK_PLATFORM))
ccflags-y += -I$(CPUFREQ_ROOT_DIR)/src/mach/$(MTK_PLATFORM)
include $(srctree)/drivers/misc/mediatek/base/power/cpufreq_v1/src/mach/$(MTK_PLATFORM)/Makefile
endif
endif
endif
endif
endif
endif

ifeq ($(CONFIG_MACH_MT6781),y)
ccflags-y += \
        -I$(CPUFREQ_ROOT_DIR)/inc \
        -I$(srctree)/drivers/misc/mediatek/include/mt-plat/mt6781/include \
        -I$(srctree)/drivers/misc/mediatek/base/power/mt6781 \
        -I$(srctree)/drivers/misc/mediatek/base/power/include
else
ccflags-y += \
	-I$(CPUFREQ_ROOT_DIR)/inc \
	-I$(srctree)/drivers/misc/mediatek/include/mt-plat/$(CONFIG_MTK_PLATFORM)/include \
	-I$(srctree)/drivers/misc/mediatek/base/power/$(CONFIG_MTK_PLATFORM) \
	-I$(srctree)/drivers/misc/mediatek/base/power/include
endif

#sspm

ccflags-y += -I$(srctree)/drivers/misc/mediatek/sspm/
ifeq ($(CONFIG_MACH_MT6781),y)
ccflags-y += -I$(srctree)/drivers/misc/mediatek/sspm/mt6781
else
ccflags-y += -I$(srctree)/drivers/misc/mediatek/sspm/$(CONFIG_MTK_PLATFORM)
endif

ifeq ($(SSPM_VER),v2)
ccflags-y += -I$(srctree)/drivers/misc/mediatek/sspm/v2
ccflags-y += -DUSE_SSPM_VER_V2
else
ccflags-y += -I$(srctree)/drivers/misc/mediatek/sspm/v1
ccflags-y += -DUSE_SSPM_VER_V1
endif

# main
obj-y := mtk_cpufreq_main.o
obj-y += mtk_cpufreq_interface.o
obj-y += mtk_cpufreq_api.o
obj-y += mtk_cpufreq_debug.o
obj-y += mtk_cpufreq_hybrid.o

ifeq ($(CONFIG_MTK_TINYSYS_MCUPM_SUPPORT), y)
ccflags-y += -I$(srctree)/drivers/misc/mediatek/mcupm/
ccflags-y += -I$(srctree)/drivers/misc/mediatek/mcupm/$(MTK_PLATFORM)/
endif

# platform dependent files
obj-y += mach/
