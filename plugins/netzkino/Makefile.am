AM_CPPFLAGS =  \
	-I$(srcdir) \
	-I$(top_srcdir)/../neutrino2 \
	-I$(top_srcdir)/../neutrino2/src \
	-I$(top_srcdir)/../neutrino2/src/zapit/include/zapit \
	-I$(top_srcdir)/../neutrino2/lib \
	-I$(top_srcdir)/../neutrino2/lib/connection \
	-I$(top_srcdir)/../neutrino2/lib/libeventserver \
	-I$(top_srcdir)/../neutrino2/lib/libconfigfile \
	-I$(top_srcdir)/../neutrino2/lib/libnet \
	-I$(top_srcdir)/../neutrino2/lib/libxmltree \
	-I$(top_srcdir)/../neutrino2/lib/libmd5sum \
	-I$(top_srcdir)/../neutrino2/lib/libdvbapi \
	-I$(top_srcdir)/../neutrino2/lib/jsoncpp/include \
	@FREETYPE_CFLAGS@ 

noinst_LTLIBRARIES = netzkino.la

netzkino_la_SOURCES = nkparser.cpp netzkino.cpp
	 
netzkino_la_LDFLAGS = -rpath $(PLUGINDIR) -module

netzkino_la_CXXFLAGS = -fno-rtti -fno-exceptions

install-exec-local:
	install -d $(DESTDIR)$(PLUGINDIR)/netzkino
	install .libs/netzkino.so $(DESTDIR)$(PLUGINDIR)/netzkino
	install -m 0644  netzkino.cfg $(DESTDIR)$(PLUGINDIR)/netzkino
	install -m 0644  netzkino.png $(DESTDIR)$(PLUGINDIR)/netzkino
	install -m 0644  netzkino_small.png $(DESTDIR)$(PLUGINDIR)/netzkino

uninstall-local:
	-rm $(DESTDIR)$(PLUGINDIR)/netzkino/netzkino.so
	-rm $(DESTDIR)$(PLUGINDIR)/netzkino/netzkino.cfg
	-rm $(DESTDIR)$(PLUGINDIR)/netzkino/netzkino.png
	-rmdir $(DESTDIR)$(PLUGINDIR)/netzkino



