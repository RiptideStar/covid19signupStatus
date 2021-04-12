# Covid19 Vaccine Availability Finder

https://cutt.ly/myshot

The website will keep searching / checking sign-up sites for available spots every 3 mins (some spots might become available due to any cancellations).If available spots are found, registered users are notified thru email immediately.

The website allowing people to - 
1. enter their emails to be notified when a spot of covid19 vaccine is available.
2. remove their emails to unregister from the site.

## Make sign-up a service on Ubuntu Server:

1. Create /etc/init/flask.conf: 
```
description "flask"
start on stopped rc RUNLEVEL=[2345]
respawn
exec python3 /alidata/www/covid19signupStatus/signup_server.py
```

2. To start the service:
```
sudo service flask start
```
sudo service flask start/stop/status.

## Create cron job to run the check

Run it every 3 mins:
```
root@iZ238n5r3z9Z:~$ crontab -e
*/3 * * * * python3 /alidata/www/covid19signupStatus/linuxcovid19OSExtract.py >> covidsignup.log 2>&
```