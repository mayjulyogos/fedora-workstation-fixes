## Symptoms

- Brightness keys do nothing
    
- Brightness slider moves but screen brightness does not change
    
- Screen remains at maximum brightness
    
<br>

## Cause

Some NVIDIA Optimus laptops expose multiple backlight interfaces. Fedora may select the wrong interface, causing brightness controls to stop working.

<br>

## Solution

```bash
sudo nano /etc/default/grub

GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
GRUB_DEFAULT=saved
GRUB_DISABLE_SUBMENU=true
GRUB_TERMINAL_OUTPUT="console"
GRUB_CMDLINE_LINUX="rhgb quiet rd.driver.blacklist=nouveau,nova_core modprobe.blacklist=nouveau,nova_core nvidia-drm.modeset=1 nvidia-drm.fbdev=1 acpi_backlight=native"
GRUB_DISABLE_RECOVERY="true"
GRUB_ENABLE_BLSCFG=true

sudo grub2-mkconfig -o /boot/grub2/grub.cfg

reboot
```

<br>

## Explanation

The kernel parameter:

```text
acpi_backlight=native
```

forces Linux to use the native laptop backlight interface instead of alternative ACPI implementations.

<br>

## Verification

After reboot:

- Use brightness keys
    
- Move the GNOME brightness slider
    
- Confirm screen brightness changes
    

<br>

## Notes

This fix is primarily intended for NVIDIA Optimus laptops.
