ACLOCAL_AMFLAGS := -I m4

AM_CFLAGS := -Wundef \
        -Wstrict-prototypes \
        -Wno-trigraphs \
        -g -O0 \
        $(LOCBASEUTIL_CFLAGS) \
        -fno-inline \
        -fno-short-enums \
        -fpic \
        -D_GNU_SOURCE \
        -DHAVE_CONFIG_H=1 \
        -DBUILD_DIVSUFSORT64 \
        -I../android_include \
        -I../include

AM_CPPFLAGS := \
              -I. \
              -I$(WORKSPACE)/OTA/streaming/external/libbspatch/include \
              -I$(WORKSPACE)/OTA/external/libdivsufsort/android_include \
              -I$(WORKSPACE)/OTA/streaming/external/libchrome \
              -I$(WORKSPACE)/OTA/streaming/external/libbrillo \
              -I$(WORKSPACE)/OTA/streaming/external/bsdiff/include \
              -I$(WORKSPACE)/OTA/streaming/external/modp_b64 \
              -D_FILE_OFFSET_BITS=64 \
              -D_USE_RTTI_FOR_TYPE_TAGS \
              -std=c++11

AUTOMAKE_OPTIONS = subdir-objects

AM_LDFLAGS := -shared -version-info 1:0:0


libbspatch_src_la_SOURCES := bspatch.cc \
    buffer_file.cc \
    extents.cc \
    extents_file.cc \
    file.cc \
    memory_file.cc \
    sink_file.cc



library_includedir := $(pkgincludedir)


lib_LTLIBRARIES := libbspatch.la
libbspatch_la_SOURCES := $(libbspatch_src_la_SOURCES)


if USE_GLIB
libbspatch_la_CFLAGS := $(AM_CFLAGS) -DUSE_GLIB @GLIB_CFLAGS@
libbspatch_la_CPPFLAGS := $(AM_CPPFLAGS) -fpermissive -DUSE_GLIB @GLIB_CFLAGS@
libbspatch_la_LIBADD := -lm -lcurl -lssl -lmodpb64 -ldivsufsort -lcrypto -lpthread @GLIB_LIBS@
else
libbspatch_la_CFLAGS := $(AM_CFLAGS)
libbspatch_la_CPPFLAGS := $(AM_CPPFLAGS) -fpermissive
libbspatch_la_LIBADD := -lm -lcurl -lssl -lmodpb64 -lcrypto -lpthread
endif


