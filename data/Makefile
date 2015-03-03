TARGETS	= $(OBJDIR)libParser.pc
OBJDIR	=
PREFIX	= /usr/local
DESTDIR	=
RM	= rm -f
LN	= ln -f
MKDIR	= mkdir -m 0755 -p
INSTALL	= install


all: $(TARGETS)

$(OBJDIR)libParser.pc: libParser.pc.in ../config.sh
	./pkgconfig.sh -P "$(PREFIX)" -- "$(OBJDIR)libParser.pc"

clean:
	$(RM) -- $(libParser.pc_OBJS)
	./pkgconfig.sh -c -P "$(PREFIX)" -- "libParser.pc"

distclean: clean
	$(RM) -- $(TARGETS)

install: $(TARGETS)
	./pkgconfig.sh -P "$(DESTDIR)$(PREFIX)" -i -- "$(OBJDIR)libParser.pc"

uninstall:
	./pkgconfig.sh -P "$(DESTDIR)$(PREFIX)" -u -- "libParser.pc"

.PHONY: all clean distclean install uninstall
