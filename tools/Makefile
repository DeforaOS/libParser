TARGETS	= $(OBJDIR)xml
OBJDIR	=
PREFIX	= /usr/local
DESTDIR	=
BINDIR	= $(PREFIX)/bin
SBINDIR	= $(PREFIX)/sbin
CC	= cc
CPPFLAGSF= -I ../include
CPPFLAGS=
CFLAGSF	= -W `pkg-config --cflags libSystem`
CFLAGS	= -Wall -g -O2 -pedantic -fstack-protector
RM	= rm -f
LN	= ln -f
MKDIR	= mkdir -m 0755 -p
INSTALL	= install


all: $(TARGETS)

xml_OBJS = $(OBJDIR)xml.o
xml_CFLAGS = $(CPPFLAGSF) $(CPPFLAGS) $(CFLAGSF) $(CFLAGS)
xml_LDFLAGS = $(LDFLAGSF) $(LDFLAGS) -L../src `pkg-config --libs libSystem` -lParser

$(OBJDIR)xml: $(xml_OBJS)
	$(CC) -o $(OBJDIR)xml $(xml_OBJS) $(xml_LDFLAGS)

$(OBJDIR)xml.o: xml.c
	$(CC) $(xml_CFLAGS) -o $(OBJDIR)xml.o -c xml.c

clean:
	$(RM) -- $(xml_OBJS)

distclean: clean
	$(RM) -- $(TARGETS)

install: $(TARGETS)

uninstall:

.PHONY: all clean distclean install uninstall
