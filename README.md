# nagios-sous-ubuntu-20.04-LTS
Mise à jour
# apt-get update
Installation des dependances
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
# 

