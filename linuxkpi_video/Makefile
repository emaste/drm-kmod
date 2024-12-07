SRCDIR=	${.CURDIR:H}/drivers/video

.PATH:	${SRCDIR}

.include "../kconfig.mk"
.include "../linuxkpi_version.mk"

KMOD=	linuxkpi_video
SRCS=	hdmi.c \
	video_kmod.c

.if !empty(KCONFIG:MAPERTURE_HELPERS)
SRCS+= aperture.c
.endif

.if !empty(KCONFIG:MVIDEO_CMDLINE)
SRCS+=	cmdline.c
.endif

SRCS+=	bus_if.h \
	device_if.h \
	pci_if.h \
	vnode_if.h \

CFLAGS+=	-I${.CURDIR:H}/linuxkpi/gplv2/include
CFLAGS+=	-I${.CURDIR:H}/linuxkpi/bsd/include
CFLAGS+=	-I${SYSDIR}/compat/linuxkpi/common/include
CFLAGS+=	-I${SYSDIR}/compat/linuxkpi/dummy/include
CFLAGS+=	-I${.CURDIR:H}/include

CFLAGS+= '-DKBUILD_MODNAME="${KMOD}"'
CFLAGS+= '-DLINUXKPI_PARAM_PREFIX=ttm_' -DDRM_SYSCTL_PARAM_PREFIX=_${KMOD}
CFLAGS+= ${KCONFIG:C/(.*)/-DCONFIG_\1/}

CWARNFLAGS.hdmi.c=	-Wno-cast-qual

# drivers/video/aperture.c
EXPORT_SYMS+=	__aperture_remove_legacy_vga_devices
EXPORT_SYMS+=	aperture_remove_conflicting_devices
EXPORT_SYMS+=	aperture_remove_conflicting_pci_devices
EXPORT_SYMS+=	devm_aperture_acquire_for_platform_device

# drivers/video/hdmi.c
EXPORT_SYMS+=	hdmi_audio_infoframe_check
EXPORT_SYMS+=	hdmi_audio_infoframe_init
EXPORT_SYMS+=	hdmi_audio_infoframe_pack
EXPORT_SYMS+=	hdmi_audio_infoframe_pack_for_dp
EXPORT_SYMS+=	hdmi_audio_infoframe_pack_only
EXPORT_SYMS+=	hdmi_avi_infoframe_check
EXPORT_SYMS+=	hdmi_avi_infoframe_init
EXPORT_SYMS+=	hdmi_avi_infoframe_pack
EXPORT_SYMS+=	hdmi_avi_infoframe_pack_only
EXPORT_SYMS+=	hdmi_drm_infoframe_check
EXPORT_SYMS+=	hdmi_drm_infoframe_init
EXPORT_SYMS+=	hdmi_drm_infoframe_pack
EXPORT_SYMS+=	hdmi_drm_infoframe_pack_only
EXPORT_SYMS+=	hdmi_drm_infoframe_unpack_only
EXPORT_SYMS+=	hdmi_infoframe_check
EXPORT_SYMS+=	hdmi_infoframe_log
EXPORT_SYMS+=	hdmi_infoframe_pack
EXPORT_SYMS+=	hdmi_infoframe_pack_only
EXPORT_SYMS+=	hdmi_infoframe_unpack
EXPORT_SYMS+=	hdmi_spd_infoframe_check
EXPORT_SYMS+=	hdmi_spd_infoframe_init
EXPORT_SYMS+=	hdmi_spd_infoframe_pack
EXPORT_SYMS+=	hdmi_spd_infoframe_pack_only
EXPORT_SYMS+=	hdmi_vendor_infoframe_check
EXPORT_SYMS+=	hdmi_vendor_infoframe_init
EXPORT_SYMS+=	hdmi_vendor_infoframe_pack
EXPORT_SYMS+=	hdmi_vendor_infoframe_pack_only

.include <bsd.kmod.mk>
