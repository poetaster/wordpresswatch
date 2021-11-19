# wpwatch

an init script, cron.d entry, cron processing script and confgs using the inotifywait daemon to watch a wordpress installi

etc/wpwatch/files - contains a list of directories to recursiely check and those to skip
etc/init.d/wpwatch - contains ans lsb init that although called wpwatch is actuall inotify :)
etc/cron.d/wpwatch - is a simple crontab which calls ...
usr/local/bin/wpwatch.cron - checks if /var/log/wpwatch.log has been written and mails it if it has, archives the old log file
