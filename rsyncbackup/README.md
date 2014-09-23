rsync backup
============

This provides a relatively simple utility for performing regular, 
cron-based backups.  It aims to make this an easy to configure process 
that will run automatically with very minimal intervention.  The 
following features are provided:

- Configurable set of directories to back up
- Configurable directories to ignore within the directories to back up
- Uses hardlinks on backup storage to minimize space usage for unchanged 
files
- Keeps daily, weekly, monthly, and yearly backups
- Configurable number of backups to keep; automatic removal of backups 
beyond this number
- Automatic and secure rsync using ssh with keys

Installation
------------
 # make install

This Makefile supports make DESTDIR=.  You can also set sbindir and 
sysconfdir, but these may require manual configuration after install.  
In particular:

- Make sure a cron job for this is installed.  The primary 
script is DESTDIR/sbindir/backup.
- At the moment you'll need to adjust where configuration is loaded 
from.  Edit the script itself for this.

Configuration
-------------
Configuration is located in DESTDIR/sysconfdir/backup/backup.conf.  The 
following options are available:

- host: The hostanme of the rsync destination
- user: the username to use for ssh login
- idfile: The ssh private key to use to login.  You probably don't want 
this to be used for anything else - generate a new key using
 # ssh-keygen -f
Install sing ssh-copy-id or similar.
- backupdir: the location to put things on the destination machine
- backupprefix: a prefix to use on all your backups to identify them.  
Typically 'backup-', but could, for example, include the hostname.  must 
not change - changing this variable will cause the script to lose track 
of all old backups.
- dailybackup: The name to use for a daily backup.  The default value is 
correct; don't change this unless you know what you're doing.  Must 
change daily, but no less frequently
- weeklybackup: The name to use for a weekly backup.  The default value 
is correct; don't change this unless you know what you're doing.  Must 
change weekly, but no less frequently
- monthlybackup: The name to use for a monthly backup.  The default 
value is correct; don't change this unless you know what you're doing.  
Must change monthly, but no less frequently
- yearlybackup: The name to use for a yearly backup.  The default value 
is correct; don't change this unless you know what you're doing.  Must 
change yearly, but no less frequently
- {daily,weekly,monthly,yearly}keep: The number of backups of each type 
to keep.  -1 indicates to never discard any backup of this type.
- verbosity: How much output to give.  NORMAL will give output each run 
(day) on both success or failure.  QUIET gives only error output.  
VERBOSE turns on set -x and shows the commands being run.

Finally, it is recommended that you configure your cron manager to send 
mail containing the output of cron jobs.  However, this is left as an 
excercise to the reader.  (I'm not just being an academic ass, this 
configuration has a number of moving parts - do you use 
vixiecron, anacron, dcron, fcron, cronie?  postfix, ssmtp, sendmail?  
And that's without getting into site-specific things like required mail 
gateways.)

Todo
----
- Add ability to set config location from the command line.  This is key 
if DESTDIR is used to move the install to a different location and it is 
expected to run from there.
- Fix checking for cron.d; skip cron install and throw a warning if not 
found.
- Maybe set this up with autotools, so moving things is simple?  It's 
overkill, but I need the experience.
