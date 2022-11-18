# nagios4.4.6-sous-ubuntu-20.04-LTS
## Installation
### Mise à jour
```
sudo apt-get update
```
### Installation des dependances
```
sudo apt install wget unzip curl openssl build-essential libgd-dev libssl-dev libapache2-mod-php php-gd php apache2 -y
```
### Télécharger et installer Nagios-4.4.6
```
sudo wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.4.6.tar.gz
sudo tar -zxvf nagios-4.4.6.tar.gz
sudo cd nagioscore-nagios-4.4.6/
sudo ./configure
sudo make all
sudo make install-groups-users
sudo usermod -a -G nagios www-data
sudo make install
sudo make install-init
sudo make install-commandmode
sudo make install-config
sudo make install-webconf
sudo a2enmod rewrite
sudo a2enmod cgi
sudo systemctl restart apache2
sudo htpasswd -c /usr/local/nagios/etc/htpasswd.users admin
```
## Installation de Nagios Plugins
```
sudo wget https://nagios-plugins.org/download/nagios-plugins-2.3.3.tar.gz
sudo tar -zxvf nagios-plugins-2.3.3.tar.gz
sudo cd nagios-plugins-2.3.3/
sudo ./configure --with-nagios-user=nagios --with-nagios-group=nagios
sudo make
sudo make install
```
## Configuration
### Verification de la configuration Nagios
```
/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg
```
### Activer nagios
```
sudo systemctl start nagios
sudo systemctl enable nagios
```

### Ajouter HOST
```
sudo nano /usr/local/nagios/etc/servers/host.cfg
```
voici un exemple très simple du contenue de Host.cfg
```
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
```
### redemmarer Nagios
```
sudo service nagios reload
```



