# shows.pl

This is a TV show scheduler -- it has a "cron" job mode that can scrape (from epguides.com) daily TV shows that you have preconfigured in an access list.

Install:

cp shows /usr/local/bin

chmod 755 /usr/local/bin/shows

Run:

shows --init

the first time to setup the files

and then

shows --edit

to edit the last-viewed-config (LVC)

Create a file called '/etc/cron.d/runshows' that looks like this:

SHELL=/bin/bash

0 2 * * 1,3,5  root	/usr/local/bin/shows --bail --probe > /tmp/last-shows-runtime-out.txt 2>&1


To see if any shows are available today:

# shows --dump

If a show labeled "Available" has been watched, you can clear (reconcile it) with:

(See the show key names)

# shows --dump --keys 

# shows --dr keyname1,keyname2,keyname3,...

Or, to clear all of them:

# shows -da

(Adding the '-d' just causes it to "dump" the new show schedule after a change)

