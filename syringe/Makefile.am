noinst_LIBRARIES = libsyringe.a

libsyringe_a_SOURCES = \
	common.c \
	libirecovery.c \
	libpartial.c \
	libpois0n.c \
	exploits/limera1n/limera1n.c \
	exploits/steaks4uce/steaks4uce.c

AM_CPPFLAGS = \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/include/resources \
	-I$(top_srcdir)/include/payloads \
	-I$(srcdir)/exploits/limera1n \
	-I$(srcdir)/exploits/steaks4uce \
	-I$(builddir)/exploits/limera1n \
	-I$(builddir)/exploits/steaks4uce \
	$(LIBUSB_CFLAGS) \
	$(LIBCURL_CFLAGS)

payload_headers = \
	exploits/limera1n/limera1n.h \
	exploits/steaks4uce/steaks4uce.h

BUILT_SOURCES = $(payload_headers)

EXTRA_DIST = \
	exploits/limera1n/limera1n.S \
	exploits/steaks4uce/steaks4uce.S

CLEANFILES = \
	exploits/limera1n/limera1n_payload.o \
	exploits/limera1n/limera1n.payload \
	exploits/limera1n/limera1n.h \
	exploits/steaks4uce/steaks4uce_payload.o \
	exploits/steaks4uce/steaks4uce.payload \
	exploits/steaks4uce/steaks4uce.h

exploits/limera1n/limera1n.h: $(srcdir)/exploits/limera1n/limera1n.S
	$(AM_V_GEN)$(MKDIR_P) $(dir $@) && \
	$(ARM_AS) $(ARM_ASFLAGS) -o $(dir $@)/limera1n_payload.o $< && \
	$(ARM_OBJCOPY) $(ARM_OBJCOPYFLAGS) $(dir $@)/limera1n_payload.o $(dir $@)/limera1n.payload && \
	$(XXD) -i $(dir $@)/limera1n.payload > $@

exploits/steaks4uce/steaks4uce.h: $(srcdir)/exploits/steaks4uce/steaks4uce.S
	$(AM_V_GEN)$(MKDIR_P) $(dir $@) && \
	$(ARM_AS) $(ARM_ASFLAGS) -o $(dir $@)/steaks4uce_payload.o $< && \
	$(ARM_OBJCOPY) $(ARM_OBJCOPYFLAGS) $(dir $@)/steaks4uce_payload.o $(dir $@)/steaks4uce.payload && \
	$(XXD) -i $(dir $@)/steaks4uce.payload > $@

libsyringe_a_DEPENDENCIES = $(payload_headers)
