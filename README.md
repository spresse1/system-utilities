autoupdate-enable
=================

A set of per-distro scripts to enable automatic updates by package managers or do automatic updates via cron (and email results, if desired)

This project is indended to give an accessible, minimal setup tool for making sure that systems stay up to date.  For some systems (eg: apt-based systems, which already have a system for this type of thing) these are scripts to enable it.

If you're running many machines (or feel this generates too much mail) there are any number of larger projects which can do much better in a large environment.  For example, chef, puppet and friends.  
In a larger environment, you might even consider setting up a nagios instance which does the appropriate checks.  (Though you could use this collection of scripts to do the actual updates, of course!)

Currently there are update scripts for the following OSes.  See each one's folder and readme for details on the capabilities and features of each.

- Gentoo Linux (emerge)
