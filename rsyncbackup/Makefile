DESTDIR=
sysconfdir=/etc
sbindir=/sbin

all:
	echo "Nothing to do here, run make install"

install:
	mkdir -p $(DESTDIR)$(sysconfdir)/backup
	touch $(DESTDIR)$(sysconfdir)/backup/dirs
	touch $(DESTDIR)$(sysconfdir)/backup/excludes
	[ ! -e $(DESTDIR)$(sysconfdir)/backup/backup.conf ] && cp ./backup.conf $(DESTDIR)$(sysconfdir)/backup/
	[ ! -e $(DESTDIR)$(sysconfdir)/cron.d/backup ] && cp ./backup.cron $(DESTDIR)$(sysconfdir)/cron.d/backup
	cp backup $(DESTDIR)$(sbindir)/
	
