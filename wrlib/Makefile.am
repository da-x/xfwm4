## automake input file for wrlib

SUBDIRS = .
DIST_SUBDIRS = $(SUBDIRS) tests

AUTOMAKE_OPTIONS =

EXTRA_DIST = tests

noinst_LTLIBRARIES = libwraster.la

include_HEADERS = wraster.h

libwraster_la_SOURCES = 	\
	imgformat.h 	\
	raster.c 	\
	alpha_combine.c \
	draw.c		\
	color.c		\
	load.c 		\
	save.c		\
	gradient.c 	\
	xpixmap.c	\
	convert.h 	\
	convert.c 	\
	context.c 	\
	misc.c 		\
	scale.c		\
	scale.h		\
	rotate.c	\
	rotate.h	\
	flip.c		\
	convolve.c	\
	save_xpm.c	\
	xutil.c		\
	xutil.h		\
	load_ppm.c

if USE_GIF
libwraster_la_SOURCES += load_gif.c
endif

if USE_JPEG
libwraster_la_SOURCES += load_jpeg.c
endif

if USE_PNG
libwraster_la_SOURCES += load_png.c
endif

if USE_TIFF
libwraster_la_SOURCES += load_tiff.c
endif

if USE_XPM
libwraster_la_SOURCES += load_xpm.c
else
libwraster_la_SOURCES += load_xpm_normalized.c
endif

if USE_WEBP
libwraster_la_SOURCES += load_webp.c
endif

if USE_MAGICK
libwraster_la_SOURCES += load_magick.c
endif

AM_CFLAGS = @MAGICKFLAGS@
AM_CPPFLAGS = $(DFLAGS) @HEADER_SEARCH_PATH@

libwraster_la_LIBADD = @LIBRARY_SEARCH_PATH@ @GFXLIBS@ @MAGICKLIBS@ @XLIBS@ @LIBXMU@ -lm

DISTCLEANFILES = $(pkgconfig_DATA)

if HAVE_LD_VERSION_SCRIPT
libwraster.map: $(include_HEADERS) $(top_srcdir)/script/generate-mapfile-from-header.sh
	$(AM_V_GEN)$(top_srcdir)/script/generate-mapfile-from-header.sh \
		-n LIBWRASTER -v $(WRASTER_VERSION) $(srcdir)/$(include_HEADERS) > libwraster.map
endif
