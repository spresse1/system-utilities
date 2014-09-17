all: install

checkdeps:
	die () { echo "$@"; exit 1 ;}
	which emerge > /dev/null || die "Emerge not installed (..is this even a Gentoo system?)"
	which revdep-rebuild > /dev/null || die "Revdep-rebuild not installed. Run \"emerge gentoolkit\" to install."
	which etc-update > /dev/null || die "etc-update not installed.  Run \"emerge etc-update\" to install"
	which eselect > /dev/null || die "eselect not installed. Run \"emerge eselect\" to correct"

install: checkdeps
	cp emerge-sync /usr/local/sbin/emerge-sync
	chown root:root /usr/local/sbin/emerge-sync
	chmod 0755 /usr/local/sbin/emerge-sync
	if [ ! -e /etc/emerge-sync.conf ]; then cp emerge-sync.conf /etc; chown root:root /etc/emerge-sync.conf; chmod 0740 /etc/emerge-sync.conf; else echo "/etc/emerge-sync.conf exists; not clobbering it"; fi
	if [ ! -e /etc/cron.d/emerge-sync ]; then cp emerge-sync.cron /etc/cron.d/emerge-sync; chown root:root /etc/cron.d/emerge-sync; chmod 0755 /etc/cron.d/emerge-sync; else echo "/etc/cron.d/emerge-sync exists; not clobbering it"; fi
