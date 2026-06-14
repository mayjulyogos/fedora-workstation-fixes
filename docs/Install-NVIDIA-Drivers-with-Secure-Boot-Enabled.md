## Symptoms

- NVIDIA driver not loading
- Black screen after installing NVIDIA drivers
- Secure Boot blocks kernel modules

<br>

## Commands

### Install required packages (if not already installed)
```bash
sudo dnf install -y kmodtool akmods mokutil openssl
```

### Remove all enrolled MOK keys
```bash
sudo mokutil --reset
```

### Reboot and confirm the reset in MOK Manager
```bash
systemctl reboot -i
```



### Remove old akmods keys from disk
```bash
sudo rm -f /etc/pki/akmods/certs/*.der
sudo rm -f /etc/pki/akmods/private/*.priv
```

### Generate a new key pair
```bash
sudo kmodgenca -a -f
```

### Import the new key
```bash
sudo mokutil --import /etc/pki/akmods/certs/public_key.der
```

### Reboot and enroll the new key in MOK Manager
```bash
systemctl reboot -i
```



### Rebuild and sign NVIDIA modules
```bash
sudo akmods --force --rebuild
```

### Regenerate initramfs
```bash
sudo dracut --force
```

### Reboot
```
systemctl reboot -i
```



### Verify
```bash
mokutil --sb-state
modinfo nvidia | grep signer
nvidia-smi
```



### Reset Existing MOK Keys

```bash
sudo mokutil --reset
```

Removes existing enrolled Machine Owner Keys.



### Generate New Signing Keys

```bash
sudo kmodgenca -a -f
```

Creates a new key pair for signing NVIDIA kernel modules.



### Import Key

```bash
sudo mokutil --import /etc/pki/akmods/certs/public_key.der
```

Registers the new key with Secure Boot.



### Rebuild NVIDIA Modules

```bash
sudo akmods --force --rebuild
```

Rebuilds NVIDIA kernel modules and signs them.

<br>

## Verification

```bash
mokutil --sb-state
modinfo nvidia | grep signer
nvidia-smi
```

Expected:

- Secure Boot enabled
- NVIDIA module signed
- GPU detected
