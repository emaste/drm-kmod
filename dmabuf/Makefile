SRCDIR=	${.CURDIR:H}/drivers/dma-buf

.PATH:	${SRCDIR}

.include "../kconfig.mk"
.include "../linuxkpi_version.mk"

KMOD=	dmabuf
SRCS=	dma-buf-kmod.c \
	dma-buf.c \
	dma-fence-array.c \
	dma-fence-chain.c \
	dma-fence-unwrap.c \
	dma-fence.c \
	dma-resv.c \
	sync_file.c

SRCS+=	device_if.h \
	bus_if.h \
	vnode_if.h

CLEANFILES+= ${KMOD}.ko.full ${KMOD}.ko.debug

CFLAGS+= -I${.CURDIR:H}/linuxkpi/gplv2/include
CFLAGS+= -I${.CURDIR:H}/linuxkpi/bsd/include
CFLAGS+= -I${SYSDIR}/compat/linuxkpi/common/include
CFLAGS+= -I${SYSDIR}/compat/linuxkpi/dummy/include

CFLAGS+= '-DKBUILD_MODNAME="${KMOD}"'
CFLAGS+= ${KCONFIG:C/(.*)/-DCONFIG_\1/}

CWARNFLAGS.dma-buf.c+=	-Wno-pointer-arith

EXPORT_SYMS=	__dma_fence_unwrap_merge
EXPORT_SYMS+=	dma_buf_attach
EXPORT_SYMS+=	dma_buf_detach
EXPORT_SYMS+=	dma_buf_export
EXPORT_SYMS+=	dma_buf_fd
EXPORT_SYMS+=	dma_buf_get
EXPORT_SYMS+=	dma_buf_put
EXPORT_SYMS+=	dma_buf_map_attachment_unlocked
EXPORT_SYMS+=	dma_buf_unmap_attachment_unlocked
EXPORT_SYMS+=	dma_fence_add_callback
EXPORT_SYMS+=	dma_fence_allocate_private_stub
EXPORT_SYMS+=	dma_fence_chain_find_seqno
EXPORT_SYMS+=	dma_fence_chain_init
EXPORT_SYMS+=	dma_fence_chain_walk
EXPORT_SYMS+=	dma_fence_context_alloc
EXPORT_SYMS+=	dma_fence_get
EXPORT_SYMS+=	dma_fence_get_rcu
EXPORT_SYMS+=	dma_fence_get_rcu_safe
EXPORT_SYMS+=	dma_fence_get_stub
EXPORT_SYMS+=	dma_fence_get_stub_undefined
EXPORT_SYMS+=	dma_fence_init
EXPORT_SYMS+=	dma_fence_is_later
EXPORT_SYMS+=	dma_fence_is_signaled
EXPORT_SYMS+=	dma_fence_put
EXPORT_SYMS+=	dma_fence_remove_callback
EXPORT_SYMS+=	dma_fence_set_deadline
EXPORT_SYMS+=	dma_fence_set_error
EXPORT_SYMS+=	dma_fence_signal
EXPORT_SYMS+=	dma_fence_signal_timestamp
EXPORT_SYMS+=	dma_fence_timestamp
EXPORT_SYMS+=	dma_fence_wait
EXPORT_SYMS+=	dma_fence_wait_any_timeout
EXPORT_SYMS+=	dma_resv_fini
EXPORT_SYMS+=	dma_resv_get_singleton
EXPORT_SYMS+=	dma_resv_init
EXPORT_SYMS+=	dma_resv_iter_first
EXPORT_SYMS+=	dma_resv_iter_next
EXPORT_SYMS+=	dma_resv_reserve_fences
EXPORT_SYMS+=	dma_resv_test_signaled
EXPORT_SYMS+=	dma_resv_wait_timeout
EXPORT_SYMS+=	sync_file_create
EXPORT_SYMS+=	sync_file_get_fence
EXPORT_SYMS+=	to_dma_fence_chain

.include <bsd.kmod.mk>
