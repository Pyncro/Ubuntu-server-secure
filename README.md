# Ubuntu-server-secure


Avant de commencer, il serait plus simple d'éditer le serveur ubuntu via ssh (plus facile a copier/coller les texts).

<div align=center>
    <img width="100" height="100" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/apache.jpeg" />
    <img width="100" height="70" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/PhpMyAdmin.png" />
    <img width="100" height="100" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/mariadb.jpeg" />
    <img width="100" height="100" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/maill.jpeg" />
    <img width="100" height="100" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/monit.png" />
    <img width="100" height="100" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/munin.png" />
    <img width="100" height="100" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/logwatch.png" />
    <img width="100" height="100" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/webmin.png">

</div>


pour rendre cela possible, il vous suffit de :

1. connaître votre adresse ip `(ifconfig)`
2. installer le client open-ssh `(sudo apt-get install openssh-client)`
3. ouvrir le port ssh `(sudo ufw allow ssh)`
4. ouvrir le port 22 `(sudo ufw allow 22)`

## Linux Secured ssh login


<img src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/srl.png" />


Créer un nouveau utilisateur 
nano /etc/ssh/sshd_config
Port 22 -> 2000 {choisissez un numéro à quatre chiffres}

PermiRootLogin no
AllowUsers{tab}{nouveau utilisateur}

## Linux firewall w/Iptables

<img src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/it.png" />

Trouver une section dans votre répertoire *root* pour écrire ces deux scripts bash :

[flush](https://github.com/Pyncro/Ubuntu-server-secure/blob/main/firewall%20scripts/iptable_flush.rtf "flush.sh")
<img src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/flush.png">

[iptables](https://github.com/Pyncro/Ubuntu-server-secure/blob/main/firewall%20scripts/iptable_rules.rtf "iptables.sh")
<img src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/rules.png">

donnez-leur les droits d'administration en utilisant `(chmod +x {nom du fichier})` et puis exécutez flush.sh ensuite iptables.sh en utilisant `(bash)` ou `(./)`




## Linux firewall w/Fail2ban

<div align="center">
  <img src= "https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/f2b.png"/>
</div>

## Linux firewall w/rkhunter

```
wget [rkhunter](https://sourceforge.net/projects/rkhunter/files/rkhunter/1.4.6/rkhunter-1.4.6.tar.gz/download)
```

```
tar xzvf rkhunter*
cd rkhunter*
```

```
sudo ./installer.sh --layout /usr --install
``` 

```
apt-get update
apt-get install ruby-full
apt-get install binutils libreadline5 ssl-cert unhide.rb mailutils
```


## Php 7.4-fpm & others

```
sudo apt install php7.4-fpm
``` 

```
sudo apt install libapache2-mod-fcgid
``` 

```
sudo apt-get install curl
sudo service apache2 restart
sudo apt-get install php7.4-curl
sudo service apache2 restart
```

```
apt-get install php7.4-mcrypt
```

```
sudo apt-get -y install gcc make autoconf libc-dev pkg-config
```

```
sudo apt-get -y install libmcrypt-dev
```

## Mariadb installation

<div align="center">
  <img src="">
</div>

```
sudo apt install mariadb-server
sudo mysql_secure_installation
```

## Phpmyadmin

<div align="center">
  <img src="">
</div>

```
sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl
```

## Proftpd

## Apache2

## suexec

```
sudo apt-get install apache2-suexec
```

```
sudo apt-get install apache2-suexec-custom
```

## postfix

<div align="center">
  <img src="">
</div>

sudo DEBIAN_PRIORITY=low apt install postfix


## IMAP / POP3

<div align="center">
  <img src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/imappop.png">
</div>

```

sudo apt-get updates
sudo apt-get install dovecot-pop3d dovecot-imapd


```
## Monit

<div align="center">
  <img src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/monit.png">
</div>

## Munin

<div align="center">
  <img src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/munin.png">
</div>



## logwatch

<div align="center">
  <img width="200" height="200" src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/logwatch.png">
</div>

```
apt-get install logwatch
```

## Webmin

<div align="center">
  <img src="https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/webmin.png">
</div>

Webmin utilise le port 10000 (par défaut)

## Ssl

### Source

https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-20-04

https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps

https://www.digitalocean.com/community/tutorials/how-to-install-mariadb-on-ubuntu-20-04

https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-20-04-fr

https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-20-04-fr

https://askubuntu.com/questions/1319861/how-to-configure-apache-http-to-php-fpm-on-ubuntu-20-10
