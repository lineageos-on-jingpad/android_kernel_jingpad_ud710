ccflags-y += -DDEBUG

obj-$(CONFIG_SENSORS_TCS3430) += tcs3430.o

ifeq ($(CONFIG_SENSORS_TCS3430_WITH_LUX_CCT), y m)
tcs3430-y += tcs3430_als.o
endif
