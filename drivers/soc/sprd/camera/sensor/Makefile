BSP_BOARD_CAMERA_MODULE_CSI_VERSION = $(subst ",,$(CONFIG_BSP_BOARD_CAMERA_MODULE_CSI_VERSION))
ifeq ($(strip $(BSP_BOARD_CAMERA_MODULE_CSI_VERSION)),)
$(error BSP_BOARD_CAMERA_MODULE_CSI_VERSION not provided!)
else
$(info BSP_BOARD_CAMERA_MODULE_CSI_VERSION = $(BSP_BOARD_CAMERA_MODULE_CSI_VERSION))
endif

CSI_DIR := $(BSP_BOARD_CAMERA_MODULE_CSI_VERSION)

ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/sensor/../common
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/sensor/../interface
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/sensor/csi2/sprd/$(CSI_DIR)

obj-$(CONFIG_SPRD_CAMERA_SENSOR) += sprd_sensor.o
sprd_sensor-y := \
    sprd_sensor_core.o \
	sprd_sensor_drv.o \
    csi2/sprd/$(CSI_DIR)/csi_api.o \
	csi2/sprd/$(CSI_DIR)/csi_driver.o

ifeq ($(BSP_BOARD_CAMERA_MODULE_CSI_VERSION),r2p0v2)
sprd_sensor-y += csi2/sprd/$(CSI_DIR)/csi_access.o
else ifeq ($(BSP_BOARD_CAMERA_MODULE_CSI_VERSION),receiver_r2p1)
sprd_sensor-y += csi2/sprd/$(CSI_DIR)/dphy_drv.o
endif

ifeq ($(CONFIG_COMPAT),y)
sprd_sensor-y += compat_sensor_drv.o
endif
