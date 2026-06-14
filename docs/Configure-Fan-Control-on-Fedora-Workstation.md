## Symptoms

- Laptop runs hot
- Fans are too loud
- No custom fan curve available
- CoolerControl cannot detect hardware



## Solution

```bash
sudo dnf install lm_sensors -y
sudo sensors-detect
sensors

sudo pwmconfig

sudo dnf install dnf-plugins-core -y
sudo dnf copr enable codifryed/CoolerControl -y
sudo dnf install coolercontrol -y

sudo systemctl enable --now coolercontrold

sudo systemctl status coolercontrold
```



## Explanation

### Detect Hardware Sensors

```bash
sudo sensors-detect
```

Scans for motherboard temperature and fan monitoring chips.



### Verify Detection

```bash
sensors
```

Displays detected temperatures, voltages and fan speeds.



### Configure PWM Fan Control

```bash
sudo pwmconfig
```

Creates a custom fan control profile.



### Install CoolerControl

Provides a graphical interface for:

- Temperature monitoring
- Fan curves
- Performance profiles



## Verification

```bash
systemctl status coolercontrold
```

Expected:

```text
Active: active (running)
```



## Notes

Some laptop manufacturers lock fan control through firmware.

In those cases CoolerControl may only provide monitoring.
