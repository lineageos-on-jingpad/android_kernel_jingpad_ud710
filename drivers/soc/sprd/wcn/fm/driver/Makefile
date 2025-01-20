BSP_BOARD_UNISOC_WCN_SOCKET = $(subst ",,$(CONFIG_BSP_BOARD_UNISOC_WCN_SOCKET))
ifeq ($(filter $(strip $(BSP_BOARD_UNISOC_WCN_SOCKET)),sipc sdio pcie),)
$(error "No valid BSP_BOARD_UNISOC_WCN_SOCKET defined! Please set it to one of: sipc, sdio, pcie.")
else
$(info BSP_BOARD_UNISOC_WCN_SOCKET = $(BSP_BOARD_UNISOC_WCN_SOCKET))
endif

FM_DEVICE := fm_$(strip $(BSP_BOARD_UNISOC_WCN_SOCKET))

ccflags-y += -DDEBUG

obj-$(CONFIG_SPRD_WCN_FM) += sprd_fm.o
sprd_fm-y := \
    $(FM_DEVICE)/fmdrv_main.o \
	$(FM_DEVICE)/fmdrv_ops.o \
	$(FM_DEVICE)/fmdrv_rds_parser.o

ifeq ($(filter $(BSP_BOARD_UNISOC_WCN_SOCKET),sdio pcie),$(BSP_BOARD_UNISOC_WCN_SOCKET))
sprd_fm-y += \
    $(FM_DEVICE)/fm_rf_marlin3.o
endif
