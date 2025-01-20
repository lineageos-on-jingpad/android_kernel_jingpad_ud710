subdir-ccflags-y         += -I$(srctree)/drivers/soc/sprd/npu/imgtec/vha/../include
ccflags-y                += -I$(srctree)/drivers/soc/sprd/npu/imgtec/vha/platform
subdir-ccflags-y         += -I$(srctree)/drivers/soc/sprd/npu/imgtec/vha
ccflags-y                += -DCFG_SYS_MIRAGE
ccflags-y		         += -DHW_AX2
ccflags-y                += -DDEFAULT_SYMBOL_NAMESPACE=VHA_CORE

obj-$(CONFIG_SPRD_NPU_IMG) += npu_img_vha.o
npu_img_vha-y += vha_core.o vha_api.o vha_cnn.o vha_dbg.o vha_dev_ax2.o vha_pdump.o
npu_img_vha-y += vha_chipdep_roc1.o vha_qos_roc1.o
npu_img_vha-y += platform/vha_plat_dt.o platform/vha_plat_dt_example.o
