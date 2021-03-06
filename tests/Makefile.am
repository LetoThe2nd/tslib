#
#  tslib/tests/Makefile.am
#
#  Copyright (C) 2001 Russell King.
#
# This file is placed under the LGPL.  Please see the file
# COPYING for more details.
#
#

AM_CFLAGS               = -DTS_POINTERCAL=\"@TS_POINTERCAL@\" $(DEBUGFLAGS)
AM_CPPFLAGS		= -I$(top_srcdir)/src

if HAIKU
bin_PROGRAMS		= ts_print ts_print_raw ts_finddev ts_print_mt
endif

if WINDOWS
if SDL
bin_PROGRAMS		= ts_print ts_print_raw ts_print_mt ts_calibrate ts_test_mt
else
bin_PROGRAMS		= ts_print ts_print_raw ts_print_mt
endif
endif

if LINUX
if SDL
bin_PROGRAMS		= ts_test_mt ts_calibrate ts_print ts_print_mt ts_print_raw ts_finddev ts_verify
else
bin_PROGRAMS		= ts_test ts_test_mt ts_calibrate ts_print ts_print_mt ts_print_raw ts_harvest ts_finddev ts_verify
endif
endif

if FREEBSD
if SDL
bin_PROGRAMS		= ts_test_mt ts_calibrate ts_print ts_print_mt ts_print_raw ts_finddev
else
bin_PROGRAMS		= ts_test ts_test_mt ts_calibrate ts_print ts_print_mt ts_print_raw ts_harvest ts_finddev
endif
endif

if HURD
bin_PROGRAMS		= ts_print ts_print_raw ts_finddev ts_print_mt
endif

ts_test_SOURCES		= ts_test.c testutils.c testutils.h fbutils.h font_8x8.c font_8x16.c font.h
ts_test_LDADD		= $(top_builddir)/src/libts.la
if FREEBSD
ts_test_SOURCES		+= fbutils-bsd.c
else
ts_test_SOURCES		+= fbutils-linux.c
endif

if SDL
ts_test_mt_SOURCES	= ts_test_mt_sdl.c sdlutils.c sdlutils.h
ts_test_mt_LDADD	= $(top_builddir)/src/libts.la -lSDL2
else
ts_test_mt_SOURCES	= ts_test_mt.c testutils.c testutils.h fbutils.h font_8x8.c font_8x16.c font.h
ts_test_mt_LDADD	= $(top_builddir)/src/libts.la
if FREEBSD
ts_test_mt_SOURCES	+= fbutils-bsd.c
else
ts_test_mt_SOURCES	+= fbutils-linux.c
endif
endif

ts_print_SOURCES	= ts_print.c
ts_print_LDADD		= $(top_builddir)/src/libts.la

ts_print_mt_SOURCES	= ts_print_mt.c
ts_print_mt_LDADD	= $(top_builddir)/src/libts.la

ts_verify_SOURCES	= ts_verify.c
ts_verify_LDADD		= $(top_builddir)/src/libts.la

ts_print_raw_SOURCES	= ts_print_raw.c
ts_print_raw_LDADD	= $(top_builddir)/src/libts.la

if SDL
ts_calibrate_SOURCES	= ts_calibrate_sdl.c ts_calibrate.h ts_calibrate_common.c sdlutils.c sdlutils.h
ts_calibrate_LDADD	= $(top_builddir)/src/libts.la -lSDL2
else
ts_calibrate_SOURCES	= ts_calibrate.c ts_calibrate.h ts_calibrate_common.c fbutils.h testutils.c testutils.h font_8x8.c font_8x16.c font.h
ts_calibrate_LDADD	= $(top_builddir)/src/libts.la
if FREEBSD
ts_calibrate_SOURCES	+= fbutils-bsd.c
else
if DRM
ts_calibrate_SOURCES	+= drmutils.c
ts_calibrate_CFLAGS		= $(AM_CFLAGS) @libdrm_CFLAGS@
ts_calibrate_LDADD		+= @libdrm_LIBS@
else
ts_calibrate_SOURCES	+= fbutils-linux.c
endif
endif
endif

ts_harvest_SOURCES	= ts_harvest.c fbutils.h testutils.c testutils.h font_8x8.c font_8x16.c font.h
ts_harvest_LDADD	= $(top_builddir)/src/libts.la
if FREEBSD
ts_harvest_SOURCES	+= fbutils-bsd.c
else
ts_harvest_SOURCES	+= fbutils-linux.c
endif

ts_finddev_SOURCES      = ts_finddev.c
ts_finddev_LDADD        = $(top_builddir)/src/libts.la
