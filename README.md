rundeck-backup
==============

Tool to backup/restore a rundeck instance

Project website at https://blog.tomas.cat/en/2013/03/27/tool-manage-rundeck-backups/

Notes from the website:

It works plain simple, you just need to backup like this

[root@server ~]# ./rundeck-backup.sh backup rundeck.tar.gz
OK - backup finished successfully using /root/rundeck-backup.tar.gz

If we don’t type the file name, the backup will be written with today’s data:

[root@server ~]# ./rundeck-backup.sh backup
OK - backup finished successfully using /root/rundeck-backup-20130327.tar.gz

And for the recovery, as easy as:

[root@server ~]# ./rundeck-backup.sh restore
Rundeck service is not running, so jobs can't be restored. Do you want to start rundeck? (y/N) y
Starting rundeckd: [ DONE ]
OK - restore finished successfully using /root/rundeck-backup-20130327.tar.gz

There are also other options, to cover all scenarios I’ve thought of:

[root@server ~]# ./rundeck-backup.sh -h
rundeck_backup - v1.00
Copyleft (c) 2013 Tomàs Núñez Lirola under GPL License
This script deals with rundeck backup/recovery.

Usage: ./rundeck-backup.sh [OPTIONS...] {backup|restore} [backup_file] | -h --help

Options:
-h | --help
Print detailed help
--exclude-config
Don't backup / restore config files
--exclude-projects
Don't backup / restore project definitions
--exclude-keys
Don't backup / restore ssh key files
--exclude-jobs
Don't backup / restore job definitions
--exclude-hosts
Don't backup / restore .ssh/known_hosts file
--include-logs
Include execution logs in the backup / restore procedure (they are excluded by default)
-c | --configdir 
Change default rundeck config directory (/etc/rundeck)
-u | --user 
Change default rundeck user (rundeck)
-s | --service 
