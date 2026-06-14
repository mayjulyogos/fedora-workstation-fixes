## Purpose

Upgrade Fedora Workstation to a newer release using Fedora's official offline upgrade mechanism.

## When to Use

- Fedora 42 → Fedora 43
- Fedora 43 → Fedora 44
- Any supported Fedora major release upgrade



## Commands

```bash
sudo dnf upgrade --refresh
sudo dnf install dnf-plugin-system-upgrade

sudo dnf system-upgrade download --releasever=44 --allowerasing
sudo dnf system-upgrade reboot
```



## Explanation

### Update Current System

```bash
sudo dnf upgrade --refresh
```

Updates all installed packages before performing the major upgrade.



### Install Upgrade Plugin

```bash
sudo dnf install dnf-plugin-system-upgrade
```

Provides Fedora's official release upgrade functionality.



### Download New Release Packages

```bash
sudo dnf system-upgrade download --releasever=44 --allowerasing
```

Downloads all required packages for the target Fedora release.



### Begin Upgrade

```bash
sudo dnf system-upgrade reboot
```

Reboots into the upgrade environment and installs the new release.


## Verification

```bash
cat /etc/fedora-release
```

Expected output:

```text
Fedora Linux 44
```
