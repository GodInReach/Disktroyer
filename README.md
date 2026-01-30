# Disktroyer

Disktroyer is a Python-based graphical disk wiping utility designed to securely erase storage devices using multiple data erasure levels. It provides a full-screen Tkinter GUI, disk detection, safety confirmations, progress monitoring, and a generated certificate of erasure after completion.

This tool is intended for educational, lab, and controlled environments. Improper use can result in permanent data loss.

---

## Features

- Full-screen graphical interface built with Tkinter  
- Automatic detection of connected disks (HDD, SSD, NVMe)  
- Displays detailed disk information:
  - Device name and size
  - Drive type and transport
  - Model and serial number
  - Filesystem and mount status
- Three data erasure levels:
  - Low (Fast)
  - Medium (Moderate)
  - High (Secure)
- Automatic unmounting of disk partitions
- Real-time wipe progress logging
- Demo mode for safe testing
- Generates a secure certificate of erasure with SHA-256 hash
- Compliance reference: NIST SP 800-88

---

## Screens Overview

1. **Welcome Screen**
   - Lists all detected disks with icons (HDD/SSD)
   - Allows selection of a target disk

2. **Disk Details & Security Warning**
   - Shows full disk metadata
   - Displays irreversible data destruction warnings
   - Requires explicit confirmation before wiping

3. **Erasure Level Selection**
   - Low: Single pass overwrite  
   - Medium: Multiple overwrite passes  
   - High: Advanced or hardware-based secure erase (when applicable)

4. **Progress Screen**
   - Live status updates with timestamps
   - Indeterminate progress bar
   - Safety notice during wipe

5. **Certificate of Erasure**
   - Displays wipe summary
   - Includes cryptographic certificate hash

---

## Erasure Methods Used

Depending on disk type and selected level, Disktroyer may use:

- `shred`
- `dd`
- `hdparm`
- `nvme format`
- `nvme sanitize`

In demo mode, all destructive operations are simulated.

---

## Requirements

### System
- Linux-based operating system  
- Root privileges (required for actual disk wiping)  
- `lsblk`, `umount`, `shred`, `dd`, `hdparm`, `nvme-cli`

### Python
- Python 3.8 or higher

### Python Libraries
- tkinter  
- Pillow  
- reportlab (optional, for PDF certificates)  
- qrcode (optional)

Install optional dependencies:
```bash
pip install pillow reportlab qrcode
```

---

## Project Structure

```
Disktroyer/
├── img/
│   ├── Disk_WIPE.png
│   ├── HDD.png
│   ├── SSD.png
│   ├── shutdown.png
│   └── restart.png
├── GUI_backend.py
├── main.py
└── README.md
```

---

## Running the Application

```bash
sudo python3 main.py
```

Root access is mandatory for real disk erasure operations.

---

## Safety Notes

- This tool permanently destroys data.
- There is no recovery after execution.
- Always double-check the selected disk.
- Ensure backups are taken before proceeding.
- Recommended to use demo mode for testing.

---

## Demo Mode

Disktroyer runs in demo mode by default:
```python
self.demo_mode = True
```

To enable real wiping, change it to:
```python
self.demo_mode = False
```

Only disable demo mode if you fully understand the consequences.

---

## Disclaimer

Disktroyer is provided for educational and research purposes only.  
The author is not responsible for any data loss, system damage, or misuse.

