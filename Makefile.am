BUILT_SOURCES =
EXTRA_DIST =
CLEANFILES =

AM_CPPFLAGS = \
	-include $(top_builddir)/config.h
AM_CFLAGS = \
	$(my_CFLAGS) \
	$(libnmsg_CFLAGS) \
	$(libprotobuf_c_CFLAGS) \
	$(libwdns_CFLAGS)

MSG_LIBTOOL_FLAGS = -module -avoid-version

SUFFIXES = .proto .pb-c.c .pb-c.h

.proto.pb-c.c:
	$(AM_V_GEN)@PROTOC_C@ "--c_out=`pwd`" -I$(top_srcdir) $<

.proto.pb-c.h:
	$(AM_V_GEN)@PROTOC_C@ "--c_out=`pwd`" -I$(top_srcdir) $<

moduledir = $(libdir)/nmsg

nmsgsieincludedir = $(includedir)/nmsg/sie

nobase_nmsgsieinclude_HEADERS = \
	defs.h
nobase_nodist_nmsgsieinclude_HEADERS = \
	delay.pb-c.h \
	dnsdedupe.pb-c.h \
	qr.pb-c.h \
	reputation.pb-c.h

# NOTE: if the nmsg msgmod version (nmsg_msgX) changes, it must be
# updated both here and in check_libnmsg.m4.

module_LTLIBRARIES = nmsg_msg8_sie.la

nmsg_msg8_sie_la_LDFLAGS = \
	$(AM_LDFLAGS) \
	$(MSG_LIBTOOL_FLAGS)
nmsg_msg8_sie_la_LIBADD = \
	$(libnmsg_LIBS) \
	$(libwdns_LIBS)
nmsg_msg8_sie_la_SOURCES = nmsg_msg_sie.c
nodist_nmsg_msg8_sie_la_SOURCES = \
	delay.pb-c.c delay.pb-c.h \
	dnsdedupe.pb-c.c dnsdedupe.pb-c.h \
	qr.pb-c.c qr.pb-c.h \
	reputation.pb-c.c reputation.pb-c.h
BUILT_SOURCES += $(nodist_nmsg_msg8_sie_la_SOURCES)
CLEANFILES += $(nodist_nmsg_msg8_sie_la_SOURCES)
EXTRA_DIST += \
	delay.c \
	delay.proto \
	dnsdedupe.c \
	dnsdedupe.proto \
	qr.c \
	qr.proto \
	reputation.c \
	reputation.proto
