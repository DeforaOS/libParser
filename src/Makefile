TARGETS	= $(OBJDIR)libParser.a $(OBJDIR)libParser.so.0.0 $(OBJDIR)libParser.so.0 $(OBJDIR)libParser.so
OBJDIR	=
PREFIX	= /usr/local
DESTDIR	=
LIBDIR	= $(PREFIX)/lib
CC	= cc
CPPFLAGSF= -I ../include
CPPFLAGS=
CFLAGSF	= -W -fPIC
CFLAGS	= -Wall -g -O2 -pedantic
AR	= ar
RANLIB	= ranlib
CCSHARED= $(CC) -shared
RM	= rm -f
LN	= ln -f
MKDIR	= mkdir -m 0755 -p
INSTALL	= install


all: $(TARGETS)

libParser_OBJS = $(OBJDIR)xml.o
libParser_CFLAGS = $(CPPFLAGSF) $(CPPFLAGS) $(CFLAGSF) $(CFLAGS) `pkg-config --cflags libSystem`
libParser_LDFLAGS = $(LDFLAGSF) $(LDFLAGS) `pkg-config --libs libSystem`

$(OBJDIR)libParser.a: $(libParser_OBJS)
	$(AR) -rc $(OBJDIR)libParser.a $(libParser_OBJS)
	$(RANLIB) $(OBJDIR)libParser.a

$(OBJDIR)libParser.so.0.0 $(OBJDIR)libParser.so.0 $(OBJDIR)libParser.so: $(libParser_OBJS)
	$(CCSHARED) -o $(OBJDIR)libParser.so.0.0 -Wl,-soname,libParser.so.0 $(libParser_OBJS) $(libParser_LDFLAGS)
	$(LN) -s -- libParser.so.0.0 $(OBJDIR)libParser.so.0
	$(LN) -s -- libParser.so.0.0 $(OBJDIR)libParser.so

$(OBJDIR)xml.o: xml.c ../include/System/Parser/XML.h
	$(CC) $(libParser_CFLAGS) -o $(OBJDIR)xml.o -c xml.c

clean:
	$(RM) -- $(libParser_OBJS)

distclean: clean
	$(RM) -- $(TARGETS)

install: $(TARGETS)
	$(MKDIR) $(DESTDIR)$(PREFIX)/lib
	$(INSTALL) -m 0644 $(OBJDIR)libParser.a $(DESTDIR)$(PREFIX)/lib/libParser.a
	$(INSTALL) -m 0755 $(OBJDIR)libParser.so.0.0 $(DESTDIR)$(PREFIX)/lib/libParser.so.0.0
	$(LN) -s -- libParser.so.0.0 $(DESTDIR)$(PREFIX)/lib/libParser.so.0
	$(LN) -s -- libParser.so.0.0 $(DESTDIR)$(PREFIX)/lib/libParser.so

uninstall:
	$(RM) -- $(DESTDIR)$(PREFIX)/lib/libParser.a
	$(RM) -- $(DESTDIR)$(PREFIX)/lib/libParser.so.0.0
	$(RM) -- $(DESTDIR)$(PREFIX)/lib/libParser.so.0
	$(RM) -- $(DESTDIR)$(PREFIX)/lib/libParser.so

.PHONY: all clean distclean install uninstall
