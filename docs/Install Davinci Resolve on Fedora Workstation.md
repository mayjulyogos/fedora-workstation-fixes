## Symptoms

- Installer refuses to run
- Resolve launches and immediately crashes
- Resolve fails to start on Fedora

## Commands

```bash
chmod +x ./DaVinci_Resolve_20.3.2_Linux.run
sudo SKIP_PACKAGE_CHECK=1 ./DaVinci_Resolve_20.3.2_Linux.run

cd /opt/resolve/libs
sudo mkdir -p disabled-libraries
sudo mv libglib-2.0.so* libgio-2.0.so* libgmodule-2.0.so* libgobject-2.0.so* disabled-libraries/
```




## Explanation

### Skip Package Validation

```bash
sudo SKIP_PACKAGE_CHECK=1 ./DaVinci_Resolve_20.3.2_Linux.run
```

Bypasses the installer's package verification.




### Move Bundled GLib Libraries

Resolve ships older versions of several GLib libraries.

Fedora often provides newer versions that work better.

Moving the bundled libraries forces Resolve to use Fedora's versions.




## Warning

Resolve updates may restore the libraries.

If Resolve stops launching after an update, repeat this workaround.
