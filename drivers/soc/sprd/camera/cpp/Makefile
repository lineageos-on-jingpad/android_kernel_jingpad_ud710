BSP_BOARD_CAMERA_MODULE_CPP_VERSION = $(subst ",,$(CONFIG_BSP_BOARD_CAMERA_MODULE_CPP_VERSION))
ifeq ($(strip $(BSP_BOARD_CAMERA_MODULE_CPP_VERSION)),)
$(error BSP_BOARD_CAMERA_MODULE_CPP_VERSION not provided!)
else
$(info BSP_BOARD_CAMERA_MODULE_CPP_VERSION = $(BSP_BOARD_CAMERA_MODULE_CPP_VERSION))
endif

CPP_DIR := $(BSP_BOARD_CAMERA_MODULE_CPP_VERSION)

ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/cpp/../common
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/cpp/../interface

obj-$(CONFIG_SPRD_CAMERA_CPP) += sprd_cpp.o
sprd_cpp-y := $(CPP_DIR)/cpp_core.o $(CPP_DIR)/dma_drv.o $(CPP_DIR)/rot_drv.o $(CPP_DIR)/scale_drv.o

ifeq ($(CPP_DIR),lite_r6p0)
sprd_cpp-y += $(CPP_DIR)/cpp_ioctl.o
endif
