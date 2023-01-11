# Ubuntu-server-secure


Avant de commencer, il serait plus simple d'éditer le serveur ubuntu via ssh (plus facile a copier/coller les texts).


pour rendre cela possible, il vous suffit de :

1. connaître votre adresse ip `(ifconfig)`
2. installer le client open-ssh `(sudo apt-get install openssh-client)`
3. ouvrir le port ssh `(sudo ufw allow ssh)`
4. ouvrir le port 22 `(sudo ufw allow 22)`

## Linux Secured ssh login

![images](img="500" width="500" https://github.com/Pyncro/Ubuntu-server-secure/blob/main/img/srl.png)


Créer un nouveau utilisateur 
nano /etc/ssh/sshd_config
Port 22 -> 2000 {choisissez un numéro à quatre chiffres}

PermiRootLogin no
AllowUsers{tab}{nouveau utilisateur}

## Linux firewall w/Iptables

Trouver une section dans votre répertoire *root* pour écrire ces deux scripts bash :

[flush](https://github.com/Pyncro/Ubuntu-server-secure/blob/main/firewall%20scripts/iptable_flush.rtf "flush.sh")


[iptables](https://github.com/Pyncro/Ubuntu-server-secure/blob/main/firewall%20scripts/iptable_rules.rtf "iptables.sh")

donnez-leur les droits d'administration en utilisant `(chmod +x {nom du fichier})` et puis exécutez flush.sh ensuite iptables.sh en utilisant `(bash)` ou `(./)`



## Linux firewall w/Fail2ban

## Linux Firewall w/UFW

```
apt install ufw 
```

```
systemctl status ufw
```

```
sudo ufw enable
```

```
ufw default allow outgoing
ufw default deny incoming
```

```
ufw allow ssh
ufw allow 80
ufw allow 443
```

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


## Php 7.4 library

## Mariadb installation

## Phpmyadmin


### Source

https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-20-04

https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps


