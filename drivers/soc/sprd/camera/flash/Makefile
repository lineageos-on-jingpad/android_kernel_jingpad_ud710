SENSOR_NAME = $(subst ",,$(CONFIG_SPRD_CAMERA_FLASH_SENSOR_IC_NAME))
ifeq ($(strip $(SENSOR_NAME)),)
$(error SENSOR_NAME not provided!)
else
$(info SENSOR_NAME = $(SENSOR_NAME))
endif

obj-$(CONFIG_SPRD_CAMERA_FLASH_SENSOR_IC) += $(SENSOR_NAME)/
obj-$(CONFIG_SPRD_CAMERA_FLASH_DRV) += flash_drv/
