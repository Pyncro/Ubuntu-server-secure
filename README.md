# Ubuntu-server-install


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
