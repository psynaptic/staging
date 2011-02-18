# Staging

This module displays a last updated date line at the bottom of the browser
window. It works by reading a variable which is set by some other means,
usually a drush command triggered on cron.

## Cron script

The following is an example cron script which you can edit, save, make
executable and periodically trigger from your user's crontab:

    #!/bin/sh
    cd /var/www/site_name
    git pull origin master # Replace with the update command for your VCS
    /usr/local/bin/drush vset -y staging_last_update `date +%s`

## Crontab

The folowwing crontab entry will execute the cron script every 15 minutes.

    */15 * * * * sh /path/to/site_name.sh > /dev/null

