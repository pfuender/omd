include ../../../Makefile.omd

PLUGIN = check_mssql_health
VERSION = 2.6.4.12
DIR = $(PLUGIN)-$(VERSION)

build:
	tar xf $(DIR).tar.gz
	cd $(DIR) && \
	./configure && \
	$(MAKE)
	sed -e '1s|.*|#!/usr/bin/env perl|g' -i $(DIR)/plugins-scripts/$(PLUGIN)
	sed -e 's|#!\ */usr/bin/perl|#!/usr/bin/env perl|g' -i $(DIR)/plugins-scripts/$(PLUGIN)
	sed -e 's|#\ */usr/bin/perl|# /usr/bin/env perl|g' -i $(DIR)/plugins-scripts/$(PLUGIN)

install:
	[ -d $(DESTDIR)$(OMD_ROOT)/lib/nagios/plugins ] || mkdir -p $(DESTDIR)$(OMD_ROOT)/lib/nagios/plugins
	install -m 755 $(DIR)/plugins-scripts/$(PLUGIN) $(DESTDIR)$(OMD_ROOT)/lib/nagios/plugins

skel:

clean:
	rm -rf $(DIR)

