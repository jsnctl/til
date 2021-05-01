# Install `fail2ban` on Ubuntu 20.04

```
sudo apt-get install fail2ban
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local  # don't edit default jail
```

Check it's running
```
$ sudo systemctl status fail2ban

...
May 01 12:59:01 ip-172-26-0-136 systemd[1]: Started Fail2Ban Service.
May 01 12:59:01 ip-172-26-0-136 fail2ban-server[903640]: Server ready
```

See what's happening in the service
```
cat /var/log/fail2ban.log*
```

Get `nginx` logs for Docker container
```
sudo docker inspect <nginx_container_hash>
```

Copy dir in 


To configure, edit `/etc/fail2ban/jail.local` (via `nano` cos I'm a filthy casual) to have:

```
ignoreip = 127.0.0.1/8 ::1 <your_ip_address>

...

[nginx-http-auth]
enabled = true
port    = http,https
logpath = /var/snap/docker/common/var-lib-docker/containers/*/*-json.log

[nginx-botsearch]
enabled = true
port     = http,https
logpath = /var/snap/docker/common/var-lib-docker/containers/*/*-json.log
maxretry = 2
```

Restart fail2ban
```
sudo systemctl restart fail2ban
```

Check all is good
```
$ sudo fail2ban-client status

Status
|- Number of jail:	3
`- Jail list:	nginx-botsearch, nginx-http-auth, sshd
```



