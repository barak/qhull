all::

include ../Makefile.prefix

all install clean uninstall::
	$(MAKE) -C liba $@
	$(MAKE) -C libso $@
	$(MAKE) -f Makefile.bins $@

hsrc = geom.h io.h mem.h merge.h poly.h qhull.h qhull_a.h qset.h stat.h user.h

install::
	-install --directory $(DESTDIR)$(includedir)/qhull
	$(INSTALL_DATA) $(hsrc) $(DESTDIR)$(includedir)/qhull/

.PHONY: all install install-strip clean uninstall
