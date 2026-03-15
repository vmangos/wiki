Here is a list of steps to make VMaNGOS run on Linux. Guide by Florian.

### Installed Devuan ASCII 2.0

https://devuan.org/devuan_ascii/installer-iso/devuan_ascii_2.0.0_amd64_netinst.iso

Only SSH-server and Standard Utils.

### *Optional*

Since I will run the server without a monitor attached, I will make use of PuTTY, so I can do all the work from my main (windows) machine.

https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

For this to work, it is needed to install SSH.

**install mc**

```
apt-get install mc
```

**Prepare SSH for public key authentication**

https://www.howtoforge.com/ssh_key_based_logins_putty_p2

```
mkdir ~/.ssh
nano ~/.ssh/authorized_keys
chmod 700 ~/.ssh && chmod 600 ~/.ssh/*
nano /etc/ssh/sshd_config
Banner /etc/issue.net
nano /etc/issue.net
```

Example:

```
You have reached private server SERVERNAME.

 Notice:
 ==============================================
   This is a private server.
   All connections are monitored and recorded.
 ==============================================
   Access to this system is not permitted
   unless you have been given permission in
   person by the owner of this system.
   All others must disconnect immediately.
 
   If you have advice to share to improve the
   security or any other aspect of this system
   you can send an email to the following
   addres: YOUR@EMAIL.ADDRESS
  ==============================================
```

```
nano /etc/motd
```

```
    Welcome to

SERVERNAME private server
```

### INSTALL WEBMIN

I also like to use Webmin, an handy help for server admins. And since I am lazy, I do all as root, so if you are not root, type sudo before each line, as appropriate. 

```
nano /etc/apt/sources.list.d/Webmin.list
deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib
cp /etc/apt/sources.list.d/Webmin.list /etc/apt/sources.list.d/Webmin.list.save
cd /root
wget http://www.webmin.com/jcameron-key.asc
apt-key add jcameron-key.asc
apt-get update
apt-get install webmin
```

**install smartmon tools, curl, git**

Webmin will use these: 

```
apt-get install smartmontools curl git
```

**Remove a message in cron**

```
nano /etc/pam.d/common-session-noninteractive
```

Look for the following line: 

```
session required        pam_unix.so
```

*Above* this line, add the following: 

```
session     [success=1 default=ignore] pam_succeed_if.so service in cron quiet use_uid
```

Restart cron: 

```
service cron restart
```

*/Optional ends here*

### Install MaNGOS

**Update system**

```
export DEBIAN_FRONTEND=noninteractive
export DEBIAN_PRIORITY=critical
apt-get -qy update &&
apt-get -qy -o "Dpkg::Options::=--force-confdef" -o "Dpkg::Options::=--force-confold" upgrade &&
apt-get -qy --with-new-pkgs upgrade &&
apt-get -qy autoclean &&
apt-get -qy autoremove
```

**Install dependencies**

```
apt-get -qy update &&
apt-get -qy install gcc g++ automake git-core autoconf make cmake patch libmysql++-dev libtool libssl-dev grep binutils zlibc libc6 libbz2-dev git libreadline-dev libboost-all-dev libncurses-dev libmariadbclient-dev-compat build-essential subversion libace-dev libtbb-dev libaio1 libaio-dev p7zip-full unrar-free &&
apt-get -qy autoclean &&
apt-get -qy autoremove
```

**Install MariaDB**

```
apt-get install mariadb-server
```

To check if it is running: 

```
service mysql status
```

**Clone vmangos**

core and database from git:

```
git clone -b development https://github.com/vmangos/core vmangos/core
git clone https://github.com/brotalnia/database vmangos/db
```

**Create DB structure**

```
echo -e "CREATE DATABASE \`realmd\`;
CREATE DATABASE \`mangos\`;
CREATE DATABASE \`characters\`;
CREATE DATABASE \`logs\`;
CREATE USER 'mangos'@'localhost' IDENTIFIED BY 'mangos';
GRANT USAGE ON *.* TO 'mangos'@'localhost';
GRANT SELECT, EXECUTE, SHOW VIEW, ALTER, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, INDEX, INSERT, REFERENCES, TRIGGER, UPDATE, LOCK TABLES  ON \`realmd\`.* TO 'mangos'@'localhost';
GRANT SELECT, EXECUTE, SHOW VIEW, ALTER, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, INDEX, INSERT, REFERENCES, TRIGGER, UPDATE, LOCK TABLES  ON \`mangos\`.* TO 'mangos'@'localhost';
GRANT SELECT, EXECUTE, SHOW VIEW, ALTER, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, INDEX, INSERT, REFERENCES, TRIGGER, UPDATE, LOCK TABLES  ON \`characters\`.* TO 'mangos'@'localhost';
GRANT SELECT, EXECUTE, SHOW VIEW, ALTER, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, INDEX, INSERT, REFERENCES, TRIGGER, UPDATE, LOCK TABLES  ON \`logs\`.* TO 'mangos'@'localhost';
FLUSH PRIVILEGES;
" > structure.sql

mysql -u root -pmangos < structure.sql
rm structure.sql
```

**Fill the DB**

```
7z x vmangos/db/world_full_08_february_2019.7z
mysql -u mangos -pmangos --database=mangos < world_full_08_february_2019.sql
rm world_full_08_february_2019.sql
mysql -u mangos -pmangos --database=characters < vmangos/core/sql/characters.sql
mysql -u mangos -pmangos --database=logs < vmangos/core/sql/logs.sql
mysql -u mangos -pmangos --database=realmd < vmangos/core/sql/logon.sql
```

In the next (long) line, you can change the 1st 127.0.0.1 to <the IP of your server machine> and the 255.255.255.0 to the netmask, or do it later with HeidiSQL. 

```
echo -e "INSERT INTO \`realmd\`.\`realmlist\` (\`name\`, \`address\`, \`localAddress\`, \`localSubnetMask\`, \`realmbuilds\`) VALUES ('VMaNGOS', '127.0.0.1', '127.0.0.1', '255.255.255.0', '5875 6005 6141');
" > db.sql
```

```
mysql -u mangos -pmangos --database=realmd < db.sql
rm db.sql
cd vmangos/core/sql/migrations
./merge.sh
mysql -u mangos -pmangos --database=mangos < world_db_updates.sql
rm world_db_updates.sql
cd ../../../..
```

**Set-up mangos user**

```
groupadd mangos -g 202
useradd -u 202 -g 202 -s /sbin/nologin -c "MaNGOS server daemon" mangos
```

Till here ca. 50 min.
Prepare to do this: heidisql

**Compile**

Ca. 1 hr.
(and get coffee, espresso per favore)

```
cd vmangos/core
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/opt/mangos/ ..
make -j4
cd ../../..
```

**Deploy server files**

```
mkdir -p /opt/mangos/etc
cd vmangos/core/build
cp src/mangosd/mangosd* /opt/mangos/
cp /opt/mangos/mangosd.conf.dist /opt/mangos/etc/mangosd.conf
cp src/realmd/realmd /opt/mangos/
cp ../src/realmd/realmd.conf.dist.in /opt/mangos/
cp /opt/mangos/realmd.conf.dist.in /opt/mangos/etc/realmd.conf
```

**Download maps**

Download maps & dbc files to /opt/mangos
I copied everything from the MaNGOS\Data-folder of windows version into /opt/mangos

```
chown -R mangos:mangos /opt/mangos
```

**Start the Realm**

```
cd /opt/mangos
./realmd
```

This terminal-window will stay open)

**And the World**

Open another terminal window 

```
cd /opt/mangos
./mangosd
```

(This terminal-window will stay open) 

**Create a GM account:**

In the mangos console type: 

```
.account create <name> <password>
.account set gmlevel <name> 6 or 3,2,1,0
```

### install screen

```
apt-get update
apt-get install screen
```

Create screen config file: 

```
nano .screenrc
```

```
# An alternative hardstatus to display a bar at the bottom listing the
# windownames and highlighting the current windowname in blue. (This is only
# enabled if there is no hardstatus setting for your terminal)
hardstatus on
hardstatus alwayslastline
hardstatus string "%{.bW}%-w%{.rW}%n %t%{-}%+w %=%{..G} %H %{..Y} %m/%d %c "
```

```
echo "screen -ls" >> .bashrc
```

**Install sudo**

```
apt-get install sudo
```

**wowserver (Command)**

```
nano /opt/mangos/wowserver
```

```
#! /bin/sh
case "$1" in
    start)
        echo "Starting wowserver"
        screen -c /root/.screenrc -dmS wowserver -t console
        sleep 0.5
        screen -S wowserver -p 0 -X stuff "top \n"
        sleep 0.5
        screen -S wowserver -X screen -t realmd
        sleep 0.5
        screen -S wowserver -p 1 -X stuff "cd /opt/mangos\n"
        screen -S wowserver -p 1 -X stuff "sudo -u mangos ./realmd\n"
        sleep 0.5
        screen -S wowserver -X screen -t mangosd
        sleep 0.5
        screen -S wowserver -p 2 -X stuff "cd /opt/mangos\n"
        screen -S wowserver -p 2 -X stuff "sudo -u mangos ./mangosd\n"
        screen -list
        echo "Type: screen -r wowserver"
        echo "to access the screens where Realmd and Mangosd are running"
        echo "."
    ;;
    stop)
        echo "Stopping wowserver"
        ps -ef | grep wowserver | grep -v grep | awk '{print $2}'| xargs kill
        echo "."
    ;;
    show)
        echo "Show wowserver"
        screen -r wowserver
        echo "."
    ;;
    *)
        echo "Usage:"
        echo "To run as a command:"
        echo "/opt/mangos/wowserver start|stop|show"
        echo "To run as a service (Daemon):"
        echo "service wowserver start|stop|show"
        exit 1
    ;;
    esac
```

make it executable: 

```
chmod a+x /opt/mangos/wowserver
```

### Make WoWserver start on boot

**wowserver (Service)**

```
nano /etc/init.d/wowserver
```

```
#! /bin/sh

### BEGIN INIT INFO
# Provides:     wowserver
# Required-Start:       networking mysql $all
# Required-Stop:
# Default-Start:        2 3 4 5
# Default-Stop:         0 1 6
# Short-Description:    WoW Server starter
# Description:  Starts the WoW Server
### END INIT INFO

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="WoW Server"
NAME=wowserver #(name of the file/daemon)
DIR=/opt/mangos
SCRIPTNAME=/etc/init.d/$NAME

cd $DIR
./wowserver
```

make it executable: 

```
chmod a+x /etc/init.d/wowserver
```

Update-rc.d to copy symlinks to all runlevels so that the WoW Server starts on bootup:

```
update-rc.d wowserver defaults
reboot
```

To enable|disable autostart: 

```
update-rc.d wowserver enable|disable
```

This can also be done with webmin, System / Bootup and Shutdown

### Install apache2

Let Webmin install Apache and not from the command-line!: 

And do Refresh Modules, and now Apache should be availlable under: Servers

**PHP**

```
apt-get install php php7.0-mysql php7.0-curl
```

Verify the PHP version using the following command. 
```
php -v
nano /var/www/html/info.php
<?php
phpinfo();
```

and check in browser 

```
php --version
```

to check if it has: with Zend OPcache

```
service apache2 restart
```

(Do it via webmin) 

**Uploading website**

Use SFTP-program to upload the website. 

**HeidiSQL**

Now that the database is filled and has a user, HeidiSQL can be used to access it:
https://www.heidisql.com/download.php
(You can do this while the compilation is running)

In the Session manager, make a new session and
on the 1st tab (Settings) change
Network type to: MySQL (SSH tunnel)
User to: mangos
and Password to: mangos

On the 2nd tab (SSH tunnel) change
SSH host + port to <IP address of the server machine> and 22 (for the port)
User: to <your user name on the server machine>
and Password to <your password on the server machine>

Click Save and Open.

Go to realmd , realmlist and click on the Data tab.
Double-click on the ip-address in the address colunm and change it
from 127.0.0.1 to <the IP of your server machine>
Double-click on the netmask in the netmask colunm and change it
from 255.255.255.0 to <the netmask of your server machine>
Now restart Apache: 

**restoring from backup**

Use HeidiSQL to restore the characters and realmd from backup. 

**Install ufw**

```
apt-get install ufw
ufw allow ssh
grep '^### tuple' /lib/ufw/user*.rules
grep '^### tuple' /etc/ufw/user*.rules
nano /etc/ufw/applications.d/ufw-wow
[WOW]
title=MaNGOS WoW server
description=MaNGOS WoW server
ports=3724,7878,8085/tcp
ufw allow wow
ufw allow webmin
ufw allow 'www full
ufw enable
ufw status numbered
```

### Automated Backup

**install SOAP**

```
apt-get install php7.0-soap 

service apache2 restart
```

restart the wowserver 

**save all characters**

Enable SOAP 

```
nano /opt/mangos/etc/mangosd.conf
```

```
SOAP.Enabled = 1
```

Restart the server 

```
/opt/mangos/killwowserver
/opt/mangos/runwowserver
```
```
nano /opt/mangos/saveall.php
```
```
<?php
/*
 * save all characters, before backup
 */

$username = 'adminname';
$password = 'adminpass';
$host = "localhost";
$soapport = 7878;
$command = "save all";
$client = new SoapClient(NULL,
array(
    "location" => "http://$host:$soapport/",
    "uri" => "urn:MaNGOS",
    "style" => SOAP_RPC,
    'login' => $username,
    'password' => $password
));
try {
    $result = $client->executeCommand(new SoapParam($command, "command"));
    echo "Command: ";
    echo $command;
    echo "<br />\n";
    echo "Command succeeded! Output:\n";
    echo $result;
}
catch (Exception $e)
{
    echo "Command failed! Reason:\n";
    echo $e->getMessage();
}
?>
```
**wowbackup**

```
mkdir /opt/mangos/backups
nano /opt/mangos/wowbackup
#! /bin/sh
php -f /opt/mangos/saveall.php
/usr/bin/mysqldump --user=mangos --password=mangos characters --single-transaction --quick --lock-tables=false > /opt/mangos/backups/chars__bu-$(date +%F_%R).sql
/usr/bin/mysqldump --user=mangos --password=mangos realmd --single-transaction --quick --lock-tables=false > /opt/mangos/backups/realmd_bu-$(date +%F_%R).sql
chmod a+x /opt/mangos/wowbackup
```

**cron backup**

```
nano /etc/crontab
```

E.g.: Backup runs at: 43 minutes 21 hours : 21h43 on every day of every month. 

```
43 21 * * *     root    /opt/mangos/wowbackup
```
```
service cron restart
```
