## Commands

```bash
fastfetch
hostnamectl
uname -a
stat /etc/machine-id

lscpu
sudo dmidecode --type memory
lspci
lsusb

sudo dmesg -T
journalctl -p 3 -xb
```

<br>

## Explanation

### 1. System Info & Identity
```bash
# High-level system overview (OS, kernel, CPU, GPU, memory, etc.)
fastfetch
```

```bash
# View hostname, chassis type, OS support timeline, and firmware age
hostnamectl
```

```bash
# Print full kernel details and system architecture
uname -a
```

```bash
# Find the exact installation date ("Birth" timestamp) of the OS
stat /etc/machine-id
```

<br>

### 2. Core Hardware Specs
```bash
# CPU Details: Check core counts, architecture, threads, and cache sizes
lscpu
```

```bash
# RAM Details: Check physical stick speed (MT/s), manufacturer, and layout
sudo dmidecode --type memory
```

```bash
# GPU & PCI: View discrete graphics card (RTX 4060) and internal controllers
lspci
```

```bash
# USB Devices: List all external peripherals connected via USB ports
lsusb
```

<br>

### 3. Diagnostics & Error Logs
```bash
# Print kernel boot messages with human-readable timestamps
sudo dmesg -T
```

```bash
# Show only critical errors (priority 3) from the current boot cycle
journalctl -p 3 -xb
```
