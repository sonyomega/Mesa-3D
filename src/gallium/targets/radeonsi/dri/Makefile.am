# Copyright © 2012 Intel Corporation
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice (including the next
# paragraph) shall be included in all copies or substantial portions of the
# Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
# EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
# MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
# NONINFRINGEMENT.  IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
# HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
# DEALINGS IN THE SOFTWARE.

DRI_VERSION_SCRIPT = $(srcdir)/../../r300/dri/radeon.link
include $(top_srcdir)/src/gallium/Automake.inc

AM_CFLAGS = \
	$(GALLIUM_DRI_CFLAGS)
AM_CPPFLAGS = \
	-DGALLIUM_RBUG \
	-DGALLIUM_TRACE \
	-DGALLIUM_NOOP

dridir = $(DRI_DRIVER_INSTALL_DIR)
dri_LTLIBRARIES = radeonsi_dri.la

nodist_EXTRA_radeonsi_dri_la_SOURCES = dummy.cpp
radeonsi_dri_la_SOURCES = \
	drm_target.c

radeonsi_dri_la_LDFLAGS = \
	$(GALLIUM_DRI_LINKER_FLAGS) \
	-Wl,--dynamic-list=$(srcdir)/../../r300/dri/radeon.dyn

radeonsi_dri_la_LIBADD = \
	$(top_builddir)/src/mesa/drivers/dri/common/libdricommon.la \
	$(top_builddir)/src/mesa/libmesagallium.la \
	$(top_builddir)/src/gallium/auxiliary/libgallium.la \
	$(top_builddir)/src/gallium/drivers/radeonsi/libradeonsi.la \
	$(top_builddir)/src/gallium/state_trackers/dri/drm/libdridrm.la \
	$(top_builddir)/src/gallium/winsys/radeon/drm/libradeonwinsys.la \
	$(top_builddir)/src/gallium/drivers/trace/libtrace.la \
	$(top_builddir)/src/gallium/drivers/rbug/librbug.la \
	$(top_builddir)/src/gallium/drivers/noop/libnoop.la \
	$(GALLIUM_DRI_LIB_DEPS) \
	$(RADEON_LIBS)

if HAVE_MESA_LLVM
radeonsi_dri_la_LDFLAGS += $(LLVM_LDFLAGS)
radeonsi_dri_la_LIBADD += $(LLVM_LIBS)
endif

include $(top_srcdir)/install-gallium-links.mk
