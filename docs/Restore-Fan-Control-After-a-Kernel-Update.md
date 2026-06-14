## Symptoms

- CoolerControl no longer controls fans
- Fan RPM reports zero
- Fan curves stop working

<br>

## Commands

```bash
sudo modprobe -r acer_wmi && sudo modprobe acer_wmi
```

<br>

## Explanation

Reloads the Acer WMI kernel module.

This forces Fedora to reconnect to the laptop's embedded controller.

<br>

## Verification

Open CoolerControl and confirm:

- Fan RPM is visible
- Fan curves work again

<br>

## Notes

Primarily intended for Acer laptops using the acer_wmi module.
