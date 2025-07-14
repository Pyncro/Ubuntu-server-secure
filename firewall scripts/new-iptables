#!/bin/sh

echo "🔧 Starting firewall setup..."

### Flush existing rules ###
echo "🧹 Flushing old iptables rules..."
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X

### Set default policies ###
echo "🔐 Setting default policies to DROP..."
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

### Allow loopback interface ###
echo "🔁 Allowing loopback traffic..."
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

### Drop invalid packets ###
echo "🚫 Dropping invalid packets..."
iptables -A INPUT -m conntrack --ctstate INVALID -j DROP

### Allow established and related connections ###
echo "🔄 Allowing established and related connections..."
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED -j ACCEPT

### Allow SSH ###
echo "🔐 Allowing SSH (port 22)..."
iptables -A INPUT -p tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 -m conntrack --ctstate ESTABLISHED -j ACCEPT

echo "🔐 Allowing SSH on custom port XXXX..."
iptables -A INPUT -p tcp --dport XXXX -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport XXXX -m conntrack --ctstate ESTABLISHED -j ACCEPT

### Allow HTTP ###
echo "🌐 Allowing HTTP (port 80)..."
iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 80 -m conntrack --ctstate ESTABLISHED -j ACCEPT

### Allow HTTPS ###
echo "🔒 Allowing HTTPS (port 443)..."
iptables -A INPUT -p tcp --dport 443 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 443 -m conntrack --ctstate ESTABLISHED -j ACCEPT

### Allow outgoing SMTP submission (port 587) ###
echo "📧 Allowing outgoing SMTP (port 587)..."
iptables -A OUTPUT -p tcp --dport 587 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --sport 587 -m conntrack --ctstate ESTABLISHED -j ACCEPT

### Allow incoming IMAPS (port 993) ###
echo "📨 Allowing incoming IMAPS (port 993)..."
iptables -A INPUT -p tcp --dport 993 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 993 -m conntrack --ctstate ESTABLISHED -j ACCEPT

echo "✅ Firewall rules applied successfully."
