all: install

checkdeps:
	die () { echo "$@"; exit 1 ;}
	which emerge > /dev/null || die "Emerge not installed (..is this even a Gentoo system?)"
	which revdep-rebuild > /dev/null || die "Revdep-rebuild not installed. Run \"emerge gentoolkit\" to install."
	which etc-update > /dev/null || die "etc-update not installed.  Run \"emerge etc-update\" to install"
	which eselect > /dev/null || die "eselect not installed. Run \"emerge eselect\" to correct"
	which mail > /dev/null || die "No mail transfer agent installed.  Run \"emerge virtual/mta\" to correct"

install: checkdeps
	cp emerge-sync /etc/cron.daily/emerge-sync
	chown root:root /etc/cron.daily/emerge-sync
	chmod 0755 /etc/cron.daily/emerge-sync
	if [ ! -e /etc/emerge-sync.conf ]; then cp emerge-sync.conf /etc; chown root:root /etc/emerge-sync.conf; chmod 0740 /etc/emerge-sync.conf; else echo "/etc/emerge-sync.conf exists; not clobbering it"; fi
