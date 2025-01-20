BSP_BOARD_CAMERA_MODULE_FD_VERSION = $(subst ",,$(CONFIG_BSP_BOARD_CAMERA_MODULE_FD_VERSION))
ifeq ($(strip $(BSP_BOARD_CAMERA_MODULE_FD_VERSION)),)
$(error BSP_BOARD_CAMERA_MODULE_FD_VERSION not provided!)
else
$(info BSP_BOARD_CAMERA_MODULE_FD_VERSION = $(BSP_BOARD_CAMERA_MODULE_FD_VERSION))
endif

FD_DIR := $(BSP_BOARD_CAMERA_MODULE_FD_VERSION)

ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/fd/../core/isp2.6/adpt/sharkl5pro/inc
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/fd/../core/isp2.6/inc/
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/fd/../common
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/fd/../interface
ccflags-y += -I$(srctree)/drivers/staging/android/ion

obj-$(CONFIG_SPRD_CAMERA_FD) += sprd_fd.o
sprd_fd-y := $(FD_DIR)/fd_core.o $(FD_DIR)/fd_drv.o
