# PokemonBlueTeam
Exercise repo for InfoSec course, configuring a Debian server, hardening the web and executing an stress test.

## Tools
- OVH (hosting and domain) [OVHCloud](https://ovhcloud.com)
- IP: 25.25.25.25 / Domain: [Pokemon](https://pokemon.java.cat)
- Terminal (executing commands)
- SSH (secure connection to the server) [SSH](https://man7.org/linux/man-pages/man1/ssh.1.html)
- UFW (uncomplicated firewall) [UFW](https://help.ubuntu.com/community/UFW)
- NGINX (web server)  [NGINX](https://nginx.org/en/docs/)
- Certbot LetsEncrypt (SSL certificate) [LetsEncrypt](https://letsencrypt.org/docs/)
- Locust (stress test) [Locust](https://locust.io)

## Used commands // all run with sudo
### Connecting to server
- ssh pokemon@25.25.25.25 -p 8383
### Create and configure user
- adduser pokemon2
- usermod -aG sudo pokemon2
### Configure ssh
- vim /etc/ssh/sshd_config
- Change port and PermitRootLogin
- systemctl restart sshd
### Configuring ufw
- ufw default deny incoming
- ufw allow 80/tcp && ufw allow 443/tcp && ufw allow 8392/tcp
### Install and restart Nginx
- apt install nginx -y
- systemctl start nginx && systemctl enable nginx
### Install SSL certificate
- apt install snapd
- snap install core
- snap refresh core
- snap install --classic certbot
- ufw allow 'WWW Full'
- ufw delete allow 'WWW'
- certbot --nginx -d pokemon.java.cat -d www.pokemon.java.cat
- certbot renew --dry-run

## Solution to problems
