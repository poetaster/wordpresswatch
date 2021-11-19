# wpwatch

an init script, cron.d entry, cron processing script and confgs using the inotifywait daemon to watch a wordpress installi

etc/wpwatch/files - contains a list of directories to recursiely check and those to skip

etc/init.d/wpwatch - contains ans lsb init that although called wpwatch is actuall inotify :)

etc/cron.d/wpwatch - is a simple crontab which calls ...

usr/local/bin/wpwatch.cron - checks if /var/log/wpwatch.log has been written and mails it if it has, archives the old log file

usr/local/bin/wpwatch - was the original approach which could not easily be used as a daemon, although it's handy for other things.

Don't forget to:
  * update-rc.d wpwatch defaults


  #!/usr/bin/bash
  # This script uses inotifywait to watch for changes to .php files


    inotifywait -r -m --exclude '.*\.(jpg|jpeg|png|pdf)'  -e close_write,moved_to,create,delete --timefmt '%Y:%M%D-%H:%M' --format '%T %w %e %f' /var/www/www.netzpolitik.org/htdocs |

    while IFS= read -r events; do

      echo "$events" | mailx admin@netzpolitik.org -a "FROM:mwa@netzpolitik.org" -a "SUBJECT:WPALARM!!!DEV2-Test"

    done



