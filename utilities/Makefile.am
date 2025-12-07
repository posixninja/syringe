bin_PROGRAMS = injectpois0n tetheredboot loadibec

AM_CPPFLAGS = \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/include/resources \
	-I$(top_srcdir)/include/payloads \
	$(LIBUSB_CFLAGS) \
	$(LIBCURL_CFLAGS)

common_ldadd = \
	$(top_builddir)/syringe/libsyringe.a \
	$(LIBUSB_LIBS) \
	$(LIBCURL_LIBS) \
	$(ZLIB_LIBS)

injectpois0n_SOURCES = injectpois0n.c
injectpois0n_LDADD = $(common_ldadd)

tetheredboot_SOURCES = tetheredboot.c
tetheredboot_LDADD = $(common_ldadd)

loadibec_SOURCES = loadibec.c
loadibec_LDADD = $(common_ldadd)
