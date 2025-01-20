#
# vdsp_sipc.ko
# vdsp_spipe.ko
# sprd_vdsp.ko
#

BSP_BOARD_CAMERA_MODULE_VDSP_DEVICE = $(subst ",,$(CONFIG_BSP_BOARD_CAMERA_MODULE_VDSP_DEVICE))
VDSP_DIR := $(BSP_BOARD_CAMERA_MODULE_VDSP_DEVICE)
$(info BSP_BOARD_CAMERA_MODULE_VDSP_DEVICE = $(BSP_BOARD_CAMERA_MODULE_VDSP_DEVICE))

ccflags-y += -DCONFIG_VBOOT_V2
ccflags-y += -DDEBUG
ccflags-y += -DKERNEL_VERSION_414
ccflags-y += -I$(srctree)/drivers/soc/sprd/npu/vdsp/../interface
ccflags-y += -I$(srctree)/drivers/staging/android/ion
ccflags-y += -I$(srctree)/drivers/devfreq/apsys/
ccflags-y += -I$(srctree)/drivers/devfreq/apsys/vdsp
ccflags-y += -I$(srctree)/drivers/soc/sprd/npu/vdsp/common
ccflags-y += -I$(srctree)/drivers/soc/sprd/npu/vdsp/$(VDSP_DIR)/xrp
ccflags-y += -I$(srctree)/drivers/soc/sprd/npu/vdsp/$(VDSP_DIR)/uipc/sipc/inc

ifeq ($(CONFIG_COMPAT),y)
ccflags-y += -DCONFIG_COMPAT
endif

ifeq ($(TEST_ON_HAPS),true)
ccflags-y += -DTEST_ON_HAPS
endif

#
# sprd_vdsp.ko
#
obj-$(CONFIG_SPRD_NPU_VDSP) := sprd_vdsp.o
sprd_vdsp-y := $(VDSP_DIR)/xrp/xrp_address_map.o $(VDSP_DIR)/xrp/vdsp_dvfs.o $(VDSP_DIR)/xrp/vdsp_smem.o $(VDSP_DIR)/xrp/pi_library_load.o
sprd_vdsp-y += $(VDSP_DIR)/xrp/common.o $(VDSP_DIR)/xrp/xrp_firmware.o $(VDSP_DIR)/xrp/xrp_alloc.o $(VDSP_DIR)/xrp/vdsp_log.o $(VDSP_DIR)/xrp/xrp_library_loader.o
sprd_vdsp-y += $(VDSP_DIR)/xrp/vdsp_ipi_drv.o $(VDSP_DIR)/xrp/xrp_cma_alloc.o $(VDSP_DIR)/xrp/vdsp_hw.o $(VDSP_DIR)/xrp/xrp_faceid.o $(VDSP_DIR)/xrp/xvp_main.o $(VDSP_DIR)/xrp/vdsp_trusty.o

#
# vdsp_sipc.ko
#
obj-$(CONFIG_SPRD_NPU_VDSP) += vdsp_sipc.o
vdsp_sipc-y := $(VDSP_DIR)/uipc/sipc/src/vdsp_sipc.o $(VDSP_DIR)/uipc/sipc/src/vdsp_smem_interface.o $(VDSP_DIR)/uipc/sipc/src/vdsp_smsg.o

#
# vdsp_spipe.ko
#
obj-$(CONFIG_SPRD_NPU_VDSP) += vdsp_spipe.o
vdsp_spipe-y := $(VDSP_DIR)/uipc/spipe/src/vdsp_spipe.o $(VDSP_DIR)/uipc/spipe/src/vdsp_sbuf.o
