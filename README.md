# nagios4.4.6-sous-ubuntu-20.04-LTS
## Mise à jour
```
sudo apt-get update
```
## Installation des dependances
# sudo apt install wget unzip curl openssl build-essential libgd-dev libssl-dev libapache2-mod-php php-gd php apache2 -y
Télécharger et installer Nagios-4.4.6
# wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.4.6.tar.gz
# tar -zxvf nagios-4.4.6.tar.gz
# cd nagioscore-nagios-4.4.6/
# ./configure
# make all
# make install-groups-users
# usermod -a -G nagios www-data
# make install
# make install-init
# make install-commandmode
# make install-config
# make install-webconf
# a2enmod rewrite
# a2enmod cgi
# systemctl restart apache2
# htpasswd -c /usr/local/nagios/etc/htpasswd.users admin

Installation de Nagios Plugins
# wget https://nagios-plugins.org/download/nagios-plugins-2.3.3.tar.gz
# tar -zxvf nagios-plugins-2.3.3.tar.gz
# cd nagios-plugins-2.3.3/
# ./configure --with-nagios-user=nagios --with-nagios-group=nagios
# make
# make install

Verification de la configuration Nagios
# /usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg
# systemctl start nagios
# systemctl enable nagios

Ajouter HOST
# nano /usr/local/nagios/etc/servers/host.cfg
define host {
        use                             linux-server
        host_name                       yourhost
        alias                           My first Apache server
        address                         1.2.3.4
        max_check_attempts              5
        check_period                    24x7
        notification_interval           30
        notification_period             24x7
}
# service nagios reload


