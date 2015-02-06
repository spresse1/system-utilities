DESTDIR=
sysconfdir=/etc
sbindir=/sbin

all:
	echo "Nothing to do here, run make install"

install:
	mkdir -p $(DESTDIR)$(sysconfdir)/backup
	touch $(DESTDIR)$(sysconfdir)/backup/dirs
	touch $(DESTDIR)$(sysconfdir)/backup/excludes
	[ ! -e $(DESTDIR)$(sysconfdir)/backup/backup.conf ] && cp ./backup.conf $(DESTDIR)$(sysconfdir)/backup/ || echo "$(DESTDIR)$(sysconfdir)/backup/backup.conf exists; not clobbering"
	[ ! -e $(DESTDIR)$(sysconfdir)/cron.d/backup ] && cp ./backup.cron $(DESTDIR)$(sysconfdir)/cron.d/backup || echo "$(DESTDIR)$(sysconfdir)/cron.d/backup exists, not clobbering"
	cp backup $(DESTDIR)$(sbindir)/
	
