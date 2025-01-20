BSP_BOARD_WLAN_DEVICE = $(subst ",,$(CONFIG_BSP_BOARD_WLAN_DEVICE))
BSP_BUILD_VARIANT = $(subst ",,$(CONFIG_BSP_BUILD_VARIANT))
ifeq ($(filter $(strip $(BSP_BOARD_WLAN_DEVICE)),sc2332 sc2355 marlin3_pcie),)
$(error no BSP_BOARD_WLAN_DEVICE, pls fix it !!!)
else
$(info BSP_BOARD_WLAN_DEVICE = $(BSP_BOARD_WLAN_DEVICE))
endif

WLAN_DEVICE := $(strip $(BSP_BOARD_WLAN_DEVICE))

ifeq ($(strip $(WLAN_DEVICE)),sc2332)
ccflags-y += -DDEBUG
else ifeq ($(strip $(WLAN_DEVICE)),sc2355)
ccflags-y += -DSC2355_FTR -DSC2355_TX_FILTER -DSC2355_QOS_MAP
ccflags-y += -DIBSS_SUPPORT -DIBSS_RSN_SUPPORT
ccflags-y += -DNAN_SUPPORT
ccflags-y += -DRTT_SUPPORT
ccflags-y += -DSC2355_RX_NO_LOOP
ccflags-y += -DACS_SUPPORT -DSC2355_HW_CSUM
ccflags-y += -DWMMAC_WFA_CERTIFICATION
ccflags-y += -DCOMPAT_SAMPILE_CODE
ccflags-y += -DRND_MAC_SUPPORT
ccflags-y += -DSOFTAP_HOOK
ccflags-y += -DATCMD_ASSERT
ccflags-y += -DTCPACK_DELAY_SUPPORT
  ifeq ($(strip $(BSP_BUILD_VARIANT)),userdebug)
  ccflags-y += -DCONFIG_SPRD_WCN_DEBUG
  endif
ccflags-y += -DSPLIT_STACK
else ifeq ($(strip $(WLAN_DEVICE)),marlin3_pcie)
ccflags-y += -DSC2355_FTR -DSC2355_TX_FILTER -DSC2355_QOS_MAP
ccflags-y += -DIBSS_SUPPORT -DIBSS_RSN_SUPPORT
ccflags-y += -DNAN_SUPPORT
#ccflags-y += -DRTT_SUPPORT
ccflags-y += -DACS_SUPPORT
#-DSC2355_HW_CSUM
ccflags-y += -DWMMAC_WFA_CERTIFICATION
ccflags-y += -DCOMPAT_SAMPILE_CODE
ccflags-y += -DRND_MAC_SUPPORT
ccflags-y += -DSOFTAP_HOOK
ccflags-y += -DATCMD_ASSERT
ccflags-y += -DTCPACK_DELAY_SUPPORT
#ccflags-y += -DDFS_MASTER
#ccflags-y += -DSC2355_RX_NAPI
ccflags-y += -DSPLIT_STACK
#ccflags-y += -DENABLE_PAM_WIFI
ifeq ($(strip $(BSP_BUILD_VARIANT)),userdebug)
ccflags-y += -DCONFIG_SPRD_WCN_DEBUG
endif
endif

obj-$(CONFIG_SPRD_WCN_WLAN) += sprdwl_ng.o
ifeq ($(BSP_BOARD_WLAN_DEVICE), marlin3_pcie)
sprdwl_ng-y := \
    $(WLAN_DEVICE)/11h.o $(WLAN_DEVICE)/api_version.o $(WLAN_DEVICE)/cfg80211.o $(WLAN_DEVICE)/cmdevt.o $(WLAN_DEVICE)/core_sc2355.o \
    $(WLAN_DEVICE)/debug.o $(WLAN_DEVICE)/defrag.o $(WLAN_DEVICE)/edma_test.o $(WLAN_DEVICE)/ibss.o $(WLAN_DEVICE)/if_sc2355.o \
    $(WLAN_DEVICE)/main.o $(WLAN_DEVICE)/mm.o $(WLAN_DEVICE)/msg.o $(WLAN_DEVICE)/nan.o $(WLAN_DEVICE)/npi.o $(WLAN_DEVICE)/pam_wifi.o \
    $(WLAN_DEVICE)/qos.o $(WLAN_DEVICE)/reorder.o $(WLAN_DEVICE)/rf_marlin3.o $(WLAN_DEVICE)/rnd_mac_addr.o $(WLAN_DEVICE)/rtt.o \
    $(WLAN_DEVICE)/rx_msg_sc2355.o $(WLAN_DEVICE)/softap_hook.o $(WLAN_DEVICE)/tcp_ack.o $(WLAN_DEVICE)/tracer.o $(WLAN_DEVICE)/tx_msg_sc2355.o \
    $(WLAN_DEVICE)/txrx.o $(WLAN_DEVICE)/txrx_buf_mm.o $(WLAN_DEVICE)/vendor.o $(WLAN_DEVICE)/work.o
else ifeq ($(BSP_BOARD_WLAN_DEVICE), sc2332)
sprdwl_ng-y := \
    $(WLAN_DEVICE)/cfg80211.o $(WLAN_DEVICE)/cmdevt.o $(WLAN_DEVICE)/embedded.o $(WLAN_DEVICE)/main.o $(WLAN_DEVICE)/msg.o $(WLAN_DEVICE)/npi.o \
    $(WLAN_DEVICE)/qos.o $(WLAN_DEVICE)/sipc.o $(WLAN_DEVICE)/tcp_ack.o $(WLAN_DEVICE)/txrx.o $(WLAN_DEVICE)/vendor.o $(WLAN_DEVICE)/wapi.o $(WLAN_DEVICE)/work.o
else ifeq ($(BSP_BOARD_WLAN_DEVICE), sc2355)
sprdwl_ng-y := \
    $(WLAN_DEVICE)/api_version.o $(WLAN_DEVICE)/cfg80211.o $(WLAN_DEVICE)/cmdevt.o $(WLAN_DEVICE)/core_sc2355.o $(WLAN_DEVICE)/debug.o $(WLAN_DEVICE)/defrag.o \
    $(WLAN_DEVICE)/ibss.o $(WLAN_DEVICE)/if_sc2355.o $(WLAN_DEVICE)/main.o $(WLAN_DEVICE)/mm.o $(WLAN_DEVICE)/msg.o $(WLAN_DEVICE)/nan.o $(WLAN_DEVICE)/npi.o \
    $(WLAN_DEVICE)/qos.o $(WLAN_DEVICE)/reorder.o $(WLAN_DEVICE)/rf_marlin3.o $(WLAN_DEVICE)/rnd_mac_addr.o $(WLAN_DEVICE)/rtt.o $(WLAN_DEVICE)/rx_msg_sc2355.o \
    $(WLAN_DEVICE)/softap_hook.o $(WLAN_DEVICE)/tcp_ack.o $(WLAN_DEVICE)/tracer.o $(WLAN_DEVICE)/tx_msg_sc2355.o $(WLAN_DEVICE)/txrx.o $(WLAN_DEVICE)/vendor.o $(WLAN_DEVICE)/work.o
endif
