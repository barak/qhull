l=qhull

all: lib$(l).a

VPATH=..

include ../../Makefile.prefix
include ../Makefile.libs.common

lib$(l).a: lib$(l).a($(ofiles))
	-ranlib $@

clean::
	-rm -f lib$(l).a

install: lib$(l).a
	-install --directory $(DESTDIR)$(libdir)
	$(INSTALL_DATA) lib$(l).a $(DESTDIR)$(libdir)/

uninstall:
	-rm -f $(DESTDIR)$(libdir)/lib$(l).a

.SECONDARY: $(ofiles)		# don't delete intermediate .o files
#.INTERMEDIATE: $(ofiles)	# delete intermediate .o files
