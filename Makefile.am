include $(top_srcdir)/misc/Makefile.common


if DVDNAV_ENABLE_EXAMPLES
EXAMPLES_DIR = examples
else
EXAMPLES_DIR =
endif

SUBDIRS = src $(EXAMPLES_DIR) doc misc m4

EXTRA_DIST = autogen.sh \
	     AUTHORS \
	     ChangeLog \
	     configure \
	     config.guess \
	     config.sub \
	     COPYING \
	     INSTALL \
	     install-sh \
	     libtool \
	     ltmain.sh \
	     missing \
	     README \
	     TODO

MOSTLYCLEANFILES += $(PACKAGE)_$(VERSION).tar.gz \
	$(distdir).tar.gz $(PACKAGE).tgz package_descriptions

MAINTAINERCLEANFILES += configure $(ACLOCAL_M4) config.h.in \
	ltmain.sh config.guess config.sub install-sh missing

world:
	@$(MAKE) clean all install 2> warnings.log
	test -s warnings.log || rm warnings.log

prune-cache:
	-rm -f config.cache

release-check:
	@./config.status misc/relchk.sh
	@./autogen.sh noconfig && $(SHELL) misc/relchk.sh

dist-hook:
	cp -r $(srcdir)/msvc $(distdir)/msvc
	rm -rf `find $(distdir)/msvc -name CVS`
