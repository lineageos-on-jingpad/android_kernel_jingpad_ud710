BSP_BOARD_UNISOC_WCN_SOCKET = $(subst ",,$(CONFIG_BSP_BOARD_UNISOC_WCN_SOCKET))
ifeq ($(filter $(strip $(BSP_BOARD_UNISOC_WCN_SOCKET)),sipc sdio pcie),)
$(error "No valid BSP_BOARD_UNISOC_WCN_SOCKET defined! Please set it to one of: sipc, sdio, pcie.")
else
$(info BSP_BOARD_UNISOC_WCN_SOCKET = $(BSP_BOARD_UNISOC_WCN_SOCKET))
endif

TTY_DEVICE := tty-$(strip $(BSP_BOARD_UNISOC_WCN_SOCKET))

ccflags-y += -DDEBUG

obj-$(CONFIG_SPRD_WCN_BLUETOOTH) += sprdbt_tty.o
sprdbt_tty-y := \
    $(TTY_DEVICE)/lpm.o \
	$(TTY_DEVICE)/rfkill.o \
	$(TTY_DEVICE)/tty.o \
	$(TTY_DEVICE)/alignment/sitm.o

ifeq ($(filter $(BSP_BOARD_UNISOC_WCN_SOCKET),sipc sdio),$(BSP_BOARD_UNISOC_WCN_SOCKET))
sprdbt_tty-y += \
	$(TTY_DEVICE)/dump.o
endif
