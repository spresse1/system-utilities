system-utilities
================

A set of minimal, missing-by-default tools for server/system maintence and upkeep.  The goal of these is to stay simple, istro-agnosic (as far as possible), configurable and widely applicable.

If you're running many machines (or feel this generates too much mail) there are any number of larger projects which can do much better in a large environment.  For example, chef, puppet and friends.  In a larger environment, you might even consider setting up a nagios instance which does the appropriate checks.  (though some of these utilities may still be useful!)

These utilities typically run as cron jobs and thus can be configured to send mail with their output.  In most cases they do not attempt to be quiet so that their failure to function is noticeable by the lack of email.  This may be undesirable - submit a feature request for this and I'll be happy to add in a way to make output only in exceptional conditions

Note: In general sending mail will not work by default.  To do so, you'll need to enable sending mail in your crontab (typically by editing /etc/crontab and adding MAILTO=root).   However, if your mail leaves your network, many ISPs ban sending mail on their networks without passing it through a mail hub they control.  If you have only one machine, you're on your own.  However, in a more complex environament where you control DNS on your network, consider setting up postfix on a machine, then pointing mail.your.domain there.  Then, on each machine, install ssmtp.  Change the root= line in /etc/ssmtp/ssmtp.conf to be your address and voila, you get all mail destined for root.  Note you may have to set rules to skip spam folders with your spam filtering.  You may also have to change rewrite domain if the machine sending mail doesn't have public DNS entries (I experienced this on Comcast).

I'm sure there are other ways of doing this, and I'd appreciate hearing about any that are simpler.

rsyncbackup
-----------
A fairly simple and configurable script for making nightly backups of a machine via rsync.  Uses hard links to reduce space usage for files which do not change.  Allows and automates keeing weekly, monthly and yearly backups as well.

This script can also manage removing stale backups.

gentoo-autoupdate
-----------------

A script designed to make care and feeding of portage-based systems much easier.  Syncs and emerges updates to packages and is capable of rebuilding kernels.  May someday be capable of reboots, but for now the administrator must do so manually.
