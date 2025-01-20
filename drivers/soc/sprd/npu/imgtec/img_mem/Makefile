ccflags-y += -I$(srctree)/drivers/soc/sprd/npu/imgtec/img_mem/imgmmu/mmulib
subdir-ccflags-y += -I$(srctree)/drivers/soc/sprd/npu/imgtec/img_mem/../include
ccflags-y += -DDEFAULT_SYMBOL_NAMESPACE=IMG_MEM

obj-$(CONFIG_SPRD_NPU_IMG) += npu_img_mem.o
npu_img_mem-y                           := img_mem_man.o
npu_img_mem-$(CONFIG_GENERIC_ALLOCATOR) += img_mem_carveout.o
npu_img_mem-$(CONFIG_DMA_SHARED_BUFFER) += img_mem_dmabuf.o
npu_img_mem-y                           += img_mem_unified.o 
npu_img_mem-y                           += img_mem_coherent.o
npu_img_mem-y                           += img_mem_anonymous.o
npu_img_mem-y                           += img_mem_ocm.o
npu_img_mem-y                           += img_pdump.o
npu_img_mem-y                           += imgmmu/imgmmu.o
npu_img_mem-y                           += imgmmu/kernel_heap.o
