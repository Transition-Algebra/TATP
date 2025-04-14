bin_SCRIPTS = tatp
CLEANFILES = $(bin_SCRIPTS)
EXTRA_DIST = tatp.in

do_subst = sed -e 's,[@]pkgdatadir[@],$(pkgdatadir),g' \
	       -e 's,[@]maude[@],$(M3),g'

tatp: tatp.in Makefile
	$(do_subst) < $(srcdir)/tatp.in > tatp
	chmod +x tatp
