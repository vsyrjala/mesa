

# Copyright © 2012 Laurent Carlier <lordheavym@gmail.com>
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
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
# IN THE SOFTWARE.

AM_CPPFLAGS = \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/src \
	-I$(top_srcdir)/src/gallium/include \
	-I$(top_srcdir)/src/gallium/auxiliary \
	-I$(top_srcdir)/src/mapi \
	-I$(top_builddir)/src/mapi \
	-I$(top_srcdir)/src/mesa/ \
	$(DEFINES)
AM_CFLAGS = $(PTHREAD_CFLAGS) \
	$(VISIBILITY_CFLAGS)

lib_LTLIBRARIES = lib@OSMESA_LIB@.la

nodist_EXTRA_lib@OSMESA_LIB@_la_SOURCES = dummy.cpp
lib@OSMESA_LIB@_la_SOURCES = osmesa.c

lib@OSMESA_LIB@_la_LDFLAGS = \
	-module \
	-no-undefined \
	-version-number @OSMESA_VERSION@ \
	$(GC_SECTIONS) \
	$(LD_NO_UNDEFINED)


if HAVE_SHARED_GLAPI
SHARED_GLAPI_LIB = $(top_builddir)/src/mapi/shared-glapi/libglapi.la
endif

lib@OSMESA_LIB@_la_LIBADD = \
	$(top_builddir)/src/mesa/libmesa.la \
	$(top_builddir)/src/mapi/glapi/libglapi.la \
	$(SHARED_GLAPI_LIB) \
	$(OSMESA_LIB_DEPS)

include $(top_srcdir)/install-lib-links.mk

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = osmesa.pc
