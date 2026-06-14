## Symptoms

- CoolerControl no longer controls fans
- Fan RPM reports zero
- Fan curves stop working



## Commands

```bash
sudo modprobe -r acer_wmi && sudo modprobe acer_wmi
```



## Explanation

Reloads the Acer WMI kernel module.

This forces Fedora to reconnect to the laptop's embedded controller.



## Verification

Open CoolerControl and confirm:

- Fan RPM is visible
- Fan curves work again



## Notes

Primarily intended for Acer laptops using the acer_wmi module.
