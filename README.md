[![Bluetooth](https://img.shields.io/badge/Bluetooth-0078D7?style=for-the-badge&logo=bluetooth&logoColor=white)](#)
[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](#)
[![Systemd](https://img.shields.io/badge/Systemd-003B57?style=for-the-badge&logo=systemd&logoColor=white)](#)

# Bluetooth
There is an issue that Bluetooth doesn't work in Dual booted kali over windows 11 and here is the solution for this

# Enable and Start the Bluetooth Daemon on Linux

This guide explains how to ensure the **Bluetooth daemon (`bluetoothd`)** is active and starts automatically on boot.

---

## Steps to Enable and Start the Bluetooth Daemon

### 1. Check if Bluetooth Service is Installed
Most Linux systems come with the Bluetooth daemon (`bluetoothd`) as part of the `bluez` package. Verify its installation:

For **Ubuntu/Debian**:
```bash
sudo apt install bluez
```

For **Fedora**:
```bash
sudo dnf install bluez
```

For **Arch**:
```bash
sudo pacman -S bluez
```

---

### 2. Start the Bluetooth Service
To manually start the Bluetooth service:
```bash
sudo systemctl start bluetooth
```

---

### 3. Enable the Bluetooth Service at Boot
To ensure the Bluetooth service starts automatically on boot:
```bash
sudo systemctl enable bluetooth
```

---

### 4. Verify the Status of the Bluetooth Service
Check if the service is active and running:
```bash
systemctl status bluetooth
```
You should see something similar to:
```
● bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running)
```

---

### 5. Restart the Service (If Needed)
If the service is running but not behaving as expected, restart it:
```bash
sudo systemctl restart bluetooth
```

---

### 6. Test Bluetooth Functionality
Use the following command to ensure Bluetooth is functioning:
```bash
bluetoothctl
```
Inside the `bluetoothctl` interactive shell:
- Type `power on` to enable Bluetooth.
- Type `scan on` to search for devices.
- Type `devices` to list discovered devices.

---

## Additional Configuration

### Ensure Your Bluetooth Adapter is Detected
Run the following command to check if your Bluetooth hardware is recognized:
```bash
lsusb | grep -i bluetooth
```

### Load the Bluetooth Kernel Module (If Necessary)
If the Bluetooth service fails to start, ensure the kernel module is loaded:
```bash
sudo modprobe btusb
```

### Check Logs for Errors
If issues persist, review system logs for Bluetooth:
```bash
journalctl -u bluetooth
```

---

After completing these steps, the Bluetooth daemon will be active and automatically start on boot, ensuring your system has functional Bluetooth support.
