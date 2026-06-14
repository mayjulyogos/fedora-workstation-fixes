## Symptoms

- Slow startup
- Long black screen before login
- Waiting for network services

<br>

## Warning

Desktop users are generally safe applying these changes.

Servers or systems that depend on networking during boot may not be.

<br>

## Commands

```bash
sudo systemctl disable NetworkManager-wait-online.service systemd-networkd-wait-online.service
sudo systemctl mask plymouth-quit-wait.service

sudo nano /etc/default/grub

sudo nano GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
GRUB_DEFAULT=saved
GRUB_DISABLE_SUBMENU=true
GRUB_TERMINAL_OUTPUT="console"
GRUB_CMDLINE_LINUX="rhgb quiet rd.driver.blacklist=nouveau,nova_core modprobe.blacklist=nouveau,nova_core nvidia-drm.modeset=1 nvidia-drm.fbdev=1 acpi_backlight=native 8250.nr_uarts=0"
GRUB_DISABLE_RECOVERY="true"
GRUB_ENABLE_BLSCFG=true

sudo grub2-mkconfig -o /boot/grub2/grub.cfg
sudo dracut --force

reboot

systemd-analyze critical-chain
```

<br>

## Explanation

### Disable Wait-Online Services

Prevents Fedora from waiting for a network connection before completing boot.

### Disable Plymouth Wait Service

Reduces unnecessary delay during shutdown and startup.

### Disable Serial Port Initialization

```text
8250.nr_uarts=0
```

Prevents initialization of unused serial devices.

<br>

## Verification

```bash
systemd-analyze
```

Compare boot times before and after applying the changes.
