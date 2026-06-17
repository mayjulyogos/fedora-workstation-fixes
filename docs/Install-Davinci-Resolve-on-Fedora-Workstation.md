## Symptoms

- Installer refuses to run
- Resolve launches and immediately crashes
- Resolve fails to start on Fedora

<br>

## Commands

```bash
chmod +x ./DaVinci_Resolve_20.3.2_Linux.run
sudo SKIP_PACKAGE_CHECK=1 ./DaVinci_Resolve_20.3.2_Linux.run

cd /opt/resolve/libs
sudo mkdir -p disabled-libraries
sudo mv libglib-2.0.so* libgio-2.0.so* libgmodule-2.0.so* libgobject-2.0.so* disabled-libraries/
```

<br>

## Uninstallation (Remove Leftover Configuration and App Data)
```bash
#launch the official uninstaller which is installed while installing davinci resolve
sudo rm -rf /opt/resolve
rm -rf ~/.local/share/DaVinciResolve
rm -rf ~/.config/DaVinciResolve
rm -rf ~/.blackmagic
rm -f ~/.local/share/applications/DaVinciResolve.desktop
sudo rm -f /usr/share/applications/blackmagic*.desktop
```

<br>

## Explanation

### Skip Package Validation

```bash
sudo SKIP_PACKAGE_CHECK=1 ./DaVinci_Resolve_20.3.2_Linux.run
```

Bypasses the installer's package verification.

### Removes the main directory
```bash
sudo rm -rf /opt/resolve
```

### Remove user configuration and preferences
```bash
rm -rf ~/.local/share/DaVinciResolve
```

### Remove Blackmagic Design config folders
```bash
rm -rf ~/.config/DaVinciResolve
rm -rf ~/.blackmagic
```

### Clean Up Desktop Shortcuts
```bash
rm -f ~/.local/share/applications/DaVinciResolve.desktop
sudo rm -f /usr/share/applications/blackmagic*.desktop
```

### Move Bundled GLib Libraries

Resolve ships older versions of several GLib libraries.

Fedora often provides newer versions that work better.

Moving the bundled libraries forces Resolve to use Fedora's versions.

<br>

## Warning

Resolve updates may restore the libraries.

If Resolve stops launching after an update, repeat this workaround.
