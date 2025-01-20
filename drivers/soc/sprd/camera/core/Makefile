BSP_BOARD_CAMERA_MODULE_ISP_VERSION = $(subst ",,$(CONFIG_BSP_BOARD_CAMERA_MODULE_ISP_VERSION))
ifeq ($(strip $(BSP_BOARD_CAMERA_MODULE_ISP_VERSION)),)
$(error BSP_BOARD_CAMERA_MODULE_ISP_VERSION not provided!)
else
$(info BSP_BOARD_CAMERA_MODULE_ISP_VERSION = $(BSP_BOARD_CAMERA_MODULE_ISP_VERSION))
endif

BSP_BOARD_CAMERA_MODULE_CSI_VERSION = $(subst ",,$(CONFIG_BSP_BOARD_CAMERA_MODULE_CSI_VERSION))
ifeq ($(strip $(BSP_BOARD_CAMERA_MODULE_CSI_VERSION)),)
$(error BSP_BOARD_CAMERA_MODULE_CSI_VERSION not provided!)
else
$(info BSP_BOARD_CAMERA_MODULE_CSI_VERSION = $(BSP_BOARD_CAMERA_MODULE_CSI_VERSION))
endif

BSP_BOARD_CAMERA_MODULE_ISP_ADAPT_VERSION = $(subst ",,$(CONFIG_BSP_BOARD_CAMERA_MODULE_ISP_ADAPT_VERSION))
ifeq ($(strip $(BSP_BOARD_CAMERA_MODULE_ISP_ADAPT_VERSION)),)
$(error BSP_BOARD_CAMERA_MODULE_ISP_ADAPT_VERSION not provided!)
else
$(info BSP_BOARD_CAMERA_MODULE_ISP_ADAPT_VERSION = $(BSP_BOARD_CAMERA_MODULE_ISP_ADAPT_VERSION))
endif

ISP_DIR	  := $(BSP_BOARD_CAMERA_MODULE_ISP_VERSION)
CSI_DIR   := $(BSP_BOARD_CAMERA_MODULE_CSI_VERSION)
ADAPT_DIR := $(BSP_BOARD_CAMERA_MODULE_ISP_ADAPT_VERSION)

ifeq ($(ISP_DIR),dcam_if_r4p0_isp_r6p11)
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/common
endif

ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/../common
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/../interface
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/../sensor
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/../sensor/csi2/sprd/$(CSI_DIR)
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/../flash/flash_drv
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/$(ISP_DIR)/inc
ccflags-y += -I$(srctree)/drivers/staging/android/ion

ifeq ($(ISP_DIR),dcam_r6p0_isp_r6p91)
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/$(ISP_DIR)/common
endif

ifeq ($(ISP_DIR),isp2.6)
ccflags-y += -I$(srctree)/drivers/soc/sprd/camera/core/$(ISP_DIR)/adpt/$(ADAPT_DIR)/inc
endif

ifeq ($(ADAPT_DIR), sharkl3)
ccflags-y += -DPROJ_SHARKL3
else ifeq ($(ADAPT_DIR), sharkl5pro)
ccflags-y += -DPROJ_SHARKL5PRO
else ifeq ($(ADAPT_DIR), roc1)
ccflags-y += -DPROJ_ROC1
endif

obj-$(CONFIG_SPRD_CAMERA_CORE) += sprd_camera.o

ifeq ($(ISP_DIR), dcam_r6p0_isp_r6p91)
sprd_camera-y := \
    $(ISP_DIR)/cpp/rot_drv.o \
    $(ISP_DIR)/cpp/img_scale.o \
    $(ISP_DIR)/cpp/scale_drv.o \
    $(ISP_DIR)/cpp/img_rot.o \
    $(ISP_DIR)/dcam/dcam_img.o \
    $(ISP_DIR)/dcam/dcam_drv.o \
    $(ISP_DIR)/common/cam_iommu.o \
    $(ISP_DIR)/common/gen_scale_coef.o \
    $(ISP_DIR)/common/sin_cos.o \
    $(ISP_DIR)/isp/isp_drv.o \
    $(ISP_DIR)/isp/block/isp_k_rgb_gain.o \
    $(ISP_DIR)/isp/block/isp_k_anti_flicker.o \
    $(ISP_DIR)/isp/block/isp_k_2d_lsc.o \
    $(ISP_DIR)/isp/block/isp_k_csa.o \
    $(ISP_DIR)/isp/block/isp_k_fetch.o \
    $(ISP_DIR)/isp/block/isp_k_gamma.o \
    $(ISP_DIR)/isp/block/isp_k_pre_cdn_rgb.o \
    $(ISP_DIR)/isp/block/isp_k_pstrz.o \
    $(ISP_DIR)/isp/block/isp_k_iircnr.o \
    $(ISP_DIR)/isp/block/isp_k_raw_afm.o \
    $(ISP_DIR)/isp/block/isp_k_nlm.o \
    $(ISP_DIR)/isp/block/isp_k_dispatch.o \
    $(ISP_DIR)/isp/block/isp_cfg_param.o \
    $(ISP_DIR)/isp/block/isp_k_post_cdn.o \
    $(ISP_DIR)/isp/block/isp_k_awbc.o \
    $(ISP_DIR)/isp/block/isp_k_css.o \
    $(ISP_DIR)/isp/block/isp_k_raw_aem.o \
    $(ISP_DIR)/isp/block/isp_k_bpc.o \
    $(ISP_DIR)/isp/block/isp_k_common.o \
    $(ISP_DIR)/isp/block/isp_k_edge.o \
    $(ISP_DIR)/isp/block/isp_k_cfa.o \
    $(ISP_DIR)/isp/block/isp_k_pgg.o \
    $(ISP_DIR)/isp/block/isp_k_pre_cdn.o \
    $(ISP_DIR)/isp/block/isp_k_binning4awb.o \
    $(ISP_DIR)/isp/block/isp_k_blc.o \
    $(ISP_DIR)/isp/block/isp_k_anti_flicker_new.o \
    $(ISP_DIR)/isp/block/isp_k_hua.o \
    $(ISP_DIR)/isp/block/isp_k_hist2.o \
    $(ISP_DIR)/isp/block/isp_k_bdn.o \
    $(ISP_DIR)/isp/block/isp_k_capability.o \
    $(ISP_DIR)/isp/block/isp_k_grgb.o \
    $(ISP_DIR)/isp/block/isp_k_y_gamma.o \
    $(ISP_DIR)/isp/block/isp_k_cce.o \
    $(ISP_DIR)/isp/block/isp_k_hist.o \
    $(ISP_DIR)/isp/block/isp_k_store.o \
    $(ISP_DIR)/isp/block/isp_k_brightness.o \
    $(ISP_DIR)/isp/block/isp_k_prefilter.o \
    $(ISP_DIR)/isp/block/isp_k_cdn.o \
    $(ISP_DIR)/isp/block/isp_k_hsv.o \
    $(ISP_DIR)/isp/block/isp_k_cmc10.o \
    $(ISP_DIR)/isp/block/isp_k_y_delay.o \
    $(ISP_DIR)/isp/block/isp_k_arbiter.o \
    $(ISP_DIR)/isp/isp_buf.o \
    $(ISP_DIR)/isp/isp_int.o
else ifeq ($(ISP_DIR), dcam_if_r4p0_isp_r6p11)
sprd_camera-y := \
    $(ISP_DIR)/src/cam_dbg.o \
    $(ISP_DIR)/src/dcam_buf.o \
    $(ISP_DIR)/src/dcam_core.o \
    $(ISP_DIR)/src/dcam_drv.o \
    $(ISP_DIR)/src/dcam_ioctrl.o \
    $(ISP_DIR)/src/isp_buf.o \
    $(ISP_DIR)/src/isp_cfg.o \
    $(ISP_DIR)/src/isp_cfg_param.o \
    $(ISP_DIR)/src/isp_drv.o \
    $(ISP_DIR)/src/isp_int.o \
    $(ISP_DIR)/src/isp_path.o \
    $(ISP_DIR)/src/isp_reg_default.o \
    $(ISP_DIR)/src/isp_slice.o \
    $(ISP_DIR)/src/isp_slw.o \
    $(ISP_DIR)/src/isp_statis_buf.o \
    common/cam_iommu.o \
    common/gen_scale_coef.o \
    common/cam_util.o \
    common/getyuvinput.o \
    common/sin_cos.o \
    $(ISP_DIR)/block/dcam_k_2d_lsc.o \
    $(ISP_DIR)/block/dcam_k_blc.o \
    $(ISP_DIR)/block/dcam_k_pdaf.o \
    $(ISP_DIR)/block/dcam_k_raw_aem.o \
    $(ISP_DIR)/block/isp_k_1d_lsc.o \
    $(ISP_DIR)/block/isp_k_2d_lsc.o \
    $(ISP_DIR)/block/isp_k_anti_flicker_new.o \
    $(ISP_DIR)/block/isp_k_arbiter.o \
    $(ISP_DIR)/block/isp_k_awb.o \
    $(ISP_DIR)/block/isp_k_binning.o \
    $(ISP_DIR)/block/isp_k_blc.o \
    $(ISP_DIR)/block/isp_k_bpc.o \
    $(ISP_DIR)/block/isp_k_brightness.o \
    $(ISP_DIR)/block/isp_k_capability.o \
    $(ISP_DIR)/block/isp_k_cce.o \
    $(ISP_DIR)/block/isp_k_cdn.o \
    $(ISP_DIR)/block/isp_k_cfa.o \
    $(ISP_DIR)/block/isp_k_cmc10.o \
    $(ISP_DIR)/block/isp_k_common.o \
    $(ISP_DIR)/block/isp_k_contrast.o \
    $(ISP_DIR)/block/isp_k_csa.o \
    $(ISP_DIR)/block/isp_k_dispatch.o \
    $(ISP_DIR)/block/isp_k_edge.o \
    $(ISP_DIR)/block/isp_k_fetch.o \
    $(ISP_DIR)/block/isp_k_gamma.o \
    $(ISP_DIR)/block/isp_k_grgb.o \
    $(ISP_DIR)/block/isp_k_hist.o \
    $(ISP_DIR)/block/isp_k_hist2.o \
    $(ISP_DIR)/block/isp_k_hsv.o \
    $(ISP_DIR)/block/isp_k_hue.o \
    $(ISP_DIR)/block/isp_k_iircnr.o \
    $(ISP_DIR)/block/isp_k_nlc.o \
    $(ISP_DIR)/block/isp_k_nlm.o \
    $(ISP_DIR)/block/isp_k_noise_filter.o \
    $(ISP_DIR)/block/isp_k_pgg.o \
    $(ISP_DIR)/block/isp_k_post_blc.o \
    $(ISP_DIR)/block/isp_k_post_cdn.o \
    $(ISP_DIR)/block/isp_k_pre_cdn.o \
    $(ISP_DIR)/block/isp_k_pstrz.o \
    $(ISP_DIR)/block/isp_k_raw_aem.o \
    $(ISP_DIR)/block/isp_k_raw_afm.o \
    $(ISP_DIR)/block/isp_k_rgb_dither.o \
    $(ISP_DIR)/block/isp_k_rgb_gain.o \
    $(ISP_DIR)/block/isp_k_store.o \
    $(ISP_DIR)/block/isp_k_uvd.o \
    $(ISP_DIR)/block/isp_k_y_delay.o \
    $(ISP_DIR)/block/isp_k_y_gamma.o \
    $(ISP_DIR)/block/isp_k_ynr.o \
    $(ISP_DIR)/block/isp_k_yrandom.o
else ifeq ($(ISP_DIR), isp2.6)
sprd_camera-y := \
    $(ISP_DIR)/src/isp_path.o \
    $(ISP_DIR)/src/isp_drv.o \
    $(ISP_DIR)/src/dcam_path.o \
    $(ISP_DIR)/src/cam_block.o \
    $(ISP_DIR)/src/dcam_drv.o \
    $(ISP_DIR)/src/cam_buf.o \
    $(ISP_DIR)/src/cam_trusty.o \
    $(ISP_DIR)/src/cam_scaler.o \
    $(ISP_DIR)/src/flash_core.o \
    $(ISP_DIR)/src/cam_queue.o \
    $(ISP_DIR)/src/isp_slice.o \
    $(ISP_DIR)/src/cam_debugger.o \
    $(ISP_DIR)/src/isp_core.o \
    $(ISP_DIR)/src/isp_cfg.o \
    $(ISP_DIR)/src/isp_fmcu.o \
    $(ISP_DIR)/src/cam_core.o \
    $(ISP_DIR)/src/isp_ltm.o \
    $(ISP_DIR)/src/isp_3dnr.o \
    $(ISP_DIR)/src/dcam_core.o

ifeq ($(filter $(ADAPT_DIR),qogirn6pro sharkl5pro),$(ADAPT_DIR))
sprd_camera-y += \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_3dnr_me.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_aem.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_afm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_anti_flicker.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_awbc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_bayerhist.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_blc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_bpc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_gain.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_lsc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_lscm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_pdaf.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_raw_gtm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_3dnr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_bchs.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cce.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cfa.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cmc10.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_edge.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_gamma.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_grgb.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_hist2.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_hsv.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_iircnr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ltm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_nlm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_post_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_pre_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_pstrz.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_uvd.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ygamma.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ynr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_yrandom.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_yuv_noisefilter.o
else ifeq ($(ADAPT_DIR), roc1)
sprd_camera-y += \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_3dnr_me.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_aem.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_afm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_anti_flicker.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_awbc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_bayerhist.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_blc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_bpc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_gain.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_lsc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_pdaf.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_3dnr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_bchs.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cce.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cfa.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cmc10.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_edge.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_gamma.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_grgb.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_hist2.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_hsv.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_iircnr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ltm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_nlm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_post_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_pre_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_pstrz.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_uvd.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ygamma.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ynr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_yrandom.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_yuv_noisefilter.o
else ifeq ($(ADAPT_DIR), sharkl3)
sprd_camera-y += \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_3dnr_me.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_aem.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_afm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_anti_flicker.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_awbc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_blc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_bpc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_gain.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_grgb.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_lsc.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/dcam_k_pdaf.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_3dnr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_brightness.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cce.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cfa.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_cmc10.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_contrast.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_csa.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_edge.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_gamma.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_hist.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_hist2.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_hsv.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_hue.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_iircnr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ltm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_nlm.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_post_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_pre_cdn.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_pstrz.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_uvd.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ygamma.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_ynr.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_yrandom.o \
    $(ISP_DIR)/adpt/$(ADAPT_DIR)/block/isp_k_yuv_noisefilter.o
endif # isp2.6 ADAPT_DIR block

sprd_camera-y += \
	$(ISP_DIR)/adpt/$(ADAPT_DIR)/cam_hw_if_$(ADAPT_DIR).o \
	$(ISP_DIR)/adpt/$(ADAPT_DIR)/dcam_int.o \
	$(ISP_DIR)/adpt/$(ADAPT_DIR)/dcam_reg.o \
	$(ISP_DIR)/adpt/$(ADAPT_DIR)/isp_int.o
endif

ifeq ($(CONFIG_COMPAT),y)
ifeq ($(ISP_DIR), dcam_if_r4p0_isp_r6p11)
sprd_camera-y += $(ISP_DIR)/compat/compat_isp_drv.o
else ifeq ($(ISP_DIR), isp2.6)
sprd_camera-y += $(ISP_DIR)/compat/compat_cam_drv.o
endif
endif
