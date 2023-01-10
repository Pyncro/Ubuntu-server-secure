# Ubuntu-server-secure


Avant de commencer, il serait plus simple d'éditer le serveur ubuntu via ssh (plus facile a copier/coller les texts).


pour rendre cela possible, il vous suffit de :

1.connaître votre adresse ip (ifconfig)
2.installer le client open-ssh ('sudo apt-get install openssh-client').
3.ouvrir le port ssh ('sudo ufw allow ssh')


## Linux firewall w/Iptables
## Linux firewall w/Fail2ban

## Linux Firewall w/UFW

```
apt install ufw 
```

```
systemctl status ufw
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

```
sudo ufw enable
```

## Linux firewall w/rkhunter

wget rkhunter 

apt-get install ruby-full

apt-get install binutils libreadline5 ssl-cert unhide.rb mailutils
