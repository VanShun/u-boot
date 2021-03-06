#
# Copyright (c) 2014 Google, Inc
#
# SPDX-License-Identifier:	GPL-2.0+
#

# We don't want the bootrom-helper present in a full U-Boot build, as
# this may have entered from ATF with the stack-pointer pointing to
# inaccessible/protected memory (and the bootrom-helper assumes that
# the stack-pointer is valid before switching to the U-Boot stack).
obj-spl-$(CONFIG_ROCKCHIP_BROM_HELPER) += bootrom.o
obj-tpl-$(CONFIG_ROCKCHIP_BROM_HELPER) += bootrom.o

obj-tpl-y += tpl.o
obj-spl-y += spl.o spl-boot-order.o

ifeq ($(CONFIG_SPL_BUILD)$(CONFIG_TPL_BUILD),)

# Always include boot_mode.o, as we bypass it (i.e. turn it off)
# inside of boot_mode.c when CONFIG_BOOT_MODE_REG is 0.  This way,
# we can have the preprocessor correctly recognise both 0x0 and 0
# meaning "turn it off".
obj-y += boot_mode.o
obj-y += boot_rkimg.o
obj-y += board.o
obj-y += chip_info.o
obj-y += iomem.o
obj-y += memblk.o
obj-y += hotkey.o

obj-$(CONFIG_USING_KERNEL_DTB) += kernel_dtb.o
obj-$(CONFIG_ROCKCHIP_SMCCC) += rockchip_smccc.o
obj-$(CONFIG_ROCKCHIP_VENDOR_PARTITION) += vendor.o
obj-$(CONFIG_ROCKCHIP_RESOURCE_IMAGE) += resource_img.o
obj-$(CONFIG_ROCKCHIP_DEBUGGER) += rockchip_debugger.o
endif

obj-$(CONFIG_$(SPL_TPL_)RAM) += param.o
obj-$(CONFIG_$(SPL_TPL_)RAM) += sdram.o
obj-$(CONFIG_SPL_KERNEL_BOOT) += spl_resource_img.o

obj-$(CONFIG_ROCKCHIP_PX30) += px30/
obj-$(CONFIG_ROCKCHIP_RK3036) += rk3036/
obj-$(CONFIG_ROCKCHIP_RK3066) += rk3066/
obj-$(CONFIG_ROCKCHIP_RK3128) += rk3128/
ifndef CONFIG_TPL_BUILD
obj-$(CONFIG_ROCKCHIP_RK3188) += rk3188/
endif
obj-$(CONFIG_ROCKCHIP_RK322X) += rk322x/
obj-$(CONFIG_ROCKCHIP_RK3288) += rk3288/
obj-$(CONFIG_ROCKCHIP_RK3308) += rk3308/
obj-$(CONFIG_ROCKCHIP_RK3328) += rk3328/
obj-$(CONFIG_ROCKCHIP_RK3368) += rk3368/
obj-$(CONFIG_ROCKCHIP_RK3399) += rk3399/
obj-$(CONFIG_ROCKCHIP_RK1808) += rk1808/
obj-$(CONFIG_ROCKCHIP_RV1108) += rv1108/

# Clear out SPL objects, in case this is a TPL build
obj-spl-$(CONFIG_TPL_BUILD) =

# Now add SPL/TPL objects back into the main build
obj-$(CONFIG_SPL_BUILD) += $(obj-spl-y)
obj-$(CONFIG_TPL_BUILD) += $(obj-tpl-y)

obj-$(CONFIG_ROCKCHIP_PRELOADER_ATAGS) += rk_atags.o
