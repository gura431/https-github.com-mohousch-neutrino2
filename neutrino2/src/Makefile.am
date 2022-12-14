SUBDIRS = driver system zapit timerd nhttpd sectionsd daemonc gui interfaces

AM_CPPFLAGS = \
	-I$(top_builddir) \
	-I$(top_srcdir) \
	-I$(srcdir) \
	-I$(top_srcdir)/src/zapit/include/zapit \
	-I$(top_srcdir)/src/gui/widget \
	-I$(top_srcdir)/lib \
	-I$(top_srcdir)/lib/connection \
	-I$(top_srcdir)/lib/libeventserver \
	-I$(top_srcdir)/lib/libconfigfile \
	-I$(top_srcdir)/lib/libnet \
	-I$(top_srcdir)/lib/libxmltree \
	-I$(top_srcdir)/lib/libmd5sum \
	@FREETYPE_CFLAGS@ \
	@FRIBIDI_CFLAGS@

if BOXTYPE_COOLSTREAM
AM_CPPFLAGS += -I$(top_srcdir)/src/zapit/include \
	-I$(top_srcdir)/lib/libcoolstream
else
AM_CPPFLAGS += -I$(top_srcdir)/lib/libdvbapi
if ENABLE_CI
AM_CPPFLAGS += -I$(top_srcdir)/lib/libdvbci
endif
endif

if ENABLE_GSTREAMER
AM_CPPFLAGS += @GSTREAMER_CFLAGS@
else
AM_CPPFLAGS += -I$(top_srcdir)/lib/libeplayer3/include
endif

if ENABLE_LUA
AM_CPPFLAGS += @LUA_INCLUDE@
endif

AM_CPPFLAGS += -fno-rtti -fno-exceptions

bin_PROGRAMS = neutrino

neutrino_SOURCES = neutrino_menue.cpp neutrino.cpp swig_helpers.cpp skin.cpp

neutrino_LDADD = \
	daemonc/libneutrino_daemonc.a \
	gui/bedit/libneutrino_gui_bedit.a \
	gui/libneutrino_gui.a \
	gui/widget/libneutrino_gui_widget.a \
	gui/widget/libneutrino_gui_widget2.a \
	driver/pictureviewer/libneutrino_pictureviewer.a \
	system/libneutrino_system.a \
	system/helpers.o \
	system/ytparser.o \
	system/tmdbparser.o \
	driver/libneutrino_driver.a \
	gui/movieinfo.o \
	gui/pictureviewer.o \
	gui/audioplayer.o \
	driver/audiodec/libneutrino_driver_audiodec.a \
	gui/bedit/bouqueteditor_bouquets.o \
	gui/libneutrino_gui2.a \
	sectionsd/libsectionsd.a \
	timerd/libtimerd.a \
	zapit/src/libzapit.a \
	nhttpd/libnhttpd.a \
	nhttpd/tuxboxapi/libnhttpd_tuxboxapi.a \
	nhttpd/yhttpd_mods/libyhttpdmods.a \
	nhttpd/yhttpd_core/libyhttpd.a \
	gui/video_setup.o \
	gui/psisetup.o \
	gui/alphasetup.o \
	gui/main_setup.o \
	gui/power_menu.o \
	gui/epg_menu.o \
	gui/widget/window.o \
	gui/widget/listbox.o \
	gui/widget/listframe.o \
	gui/widget/framebox.o \
	gui/widget/widget.o \
	gui/widget/menue.o \
	$(top_builddir)/lib/sectionsdclient/libsectionsdclient.a \
	$(top_builddir)/lib/timerdclient/libtimerdclient.a \
	$(top_builddir)/src/zapit/lib/libzapitclient.a \
	$(top_builddir)/lib/libconfigfile/libtuxbox-configfile.a \
	$(top_builddir)/lib/connection/libtuxbox-connection.a \
	$(top_builddir)/lib/libeventserver/libtuxbox-eventserver.a \
	$(top_builddir)/lib/libxmltree/libtuxbox-xmltree.a \
	$(top_builddir)/lib/libnet/libtuxbox-net.a \
	$(top_builddir)/lib/libmd5sum/libtuxbox-md5sum.a \
	$(top_builddir)/lib/libdvbsub/libdvbsub.a \
	$(top_builddir)/lib/libtuxtxt/libtuxtxt.a \
	$(top_builddir)/lib/jsoncpp/libjsoncpp.a \
	@CURL_LIBS@ \
	@FREETYPE_LIBS@ \
	@PNG_LIBS@ \
	@MAD_LIBS@ \
	@ID3TAG_LIBS@ \
	@PTHREAD_LIBS@ \
	@FRIBIDI_LIBS@ \
	-ljpeg -lrt -lblkid -ldl -lFLAC -lavformat -lavcodec -lavutil -lgif -lpthread -lOpenThreads

neutrino_LDFLAGS = -Wl,--export-dynamic

if !BOXTYPE_COOLSTREAM
neutrino_LDADD += $(top_builddir)/lib/libdvbapi/libdvbapi.a
if ENABLE_CI
neutrino_LDADD += $(top_builddir)/lib/libdvbci/libdvbci.a
endif
endif

if BOXTYPE_COOLSTREAM
neutrino_LDADD += \
	-lcoolstream-mt \
	-lnxp
endif

if ENABLE_GSTREAMER
neutrino_LDADD += @GSTREAMER_LIBS@
else
neutrino_LDADD += $(top_builddir)/lib/libeplayer3/libeplayer3.a
endif

# LCD display
if ENABLE_LCD
neutrino_LDADD += $(top_builddir)/lib/liblcddisplay/liblcddisplay.a
endif

if USE_OPENGL
neutrino_LDADD += \
	-lglut -lGL -lGLU -lGLEW
endif

if ENABLE_PYTHON
neutrino_LDADD += interfaces/python/libneutrino_interfaces_python.a \
	@PYTHON_LDFLAGS@
endif

if ENABLE_LUA
neutrino_LDADD += interfaces/lua/libneutrino_interfaces_lua.a \
	@LUA_LIB@
endif






	



