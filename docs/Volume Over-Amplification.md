## Purpose

Allow GNOME to boost volume above the normal 100% limit.



## Enable

```bash
gsettings set org.gnome.desktop.sound allow-volume-above-100-percent true
```



## Disable

```bash
gsettings set org.gnome.desktop.sound allow-volume-above-100-percent false
```



## Explanation

GNOME normally limits output volume to 100%.

This setting allows software amplification beyond that limit.



## Warning

High amplification levels may:

- Distort audio
- Damage speakers
- Cause hearing discomfort

Use carefully.
