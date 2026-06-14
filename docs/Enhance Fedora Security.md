## Purpose

Apply basic hardening to SSH and GRUB.

## Commands

```bash
sudo nano /etc/ssh/sshd_config
Port 2222
PermitRootLogin no
PasswordAuthentication no


sudo sshd -t
sudo semanage port -a -t ssh_port_t -p tcp 2222
sudo firewall-cmd --add-port=2222/tcp --permanent
sudo firewall-cmd --reload
sudo systemctl restart sshd
sudo systemctl status sshd


sudo grub2-setpassword #password: @#fedora linux#
```

## Explanation

### Change SSH Port

```text
Port 2222
```

Reduces automated SSH scanning.

### Disable Root Login

```text
PermitRootLogin no
```

Prevents direct root access through SSH.

### Disable Password Authentication

```text
PasswordAuthentication no
```

Forces key-based authentication.

### Protect GRUB

```bash
sudo grub2-setpassword
```

Adds password protection to GRUB configuration changes.
