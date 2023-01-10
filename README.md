# Ubuntu-server-install



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
