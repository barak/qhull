l=qhull

major=3
minor=1

shlib=lib$(l).so.$(major).$(minor)

all: $(shlib) lib$(l).so.$(major) lib$(l).so

VPATH=..

include ../../Makefile.prefix
include ../Makefile.libs.common

# See the Linux GCC HOWTO section 6.4.2.2, "ELF shared libraries"

CFLAGS += -fPIC
LDFLAGS += --shared -Wl,-soname=lib$(l).so.$(major) -s

$(shlib): $(ofiles)
	$(CC) $(LDFLAGS) -o $@ $^ $(LOADLIBES)

lib$(l).so.$(major):
	ln -sf $(shlib) lib$(l).so.$(major)

lib$(l).so:
	ln -sf lib$(l).so.$(major) lib$(l).so

clean::
	-rm -f lib$(l).so{.$(major){.$(minor),},}

install: $(shlib) lib$(l).so.$(major) lib$(l).so
	-install --directory $(DESTDIR)$(libdir)
	$(INSTALL_DATA) $(shlib) $(DESTDIR)$(libdir)/
	cp -af lib$(l).so{.$(major),} $(DESTDIR)$(libdir)/

uninstall:
	-rm -f $(DESTDIR)$(libdir)/lib$(l).so{.$(major){,.$(minor)},}
