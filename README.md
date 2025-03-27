Виконала самостійно Слобожан Софія РПЗ-23А

# work_case-5

# Peripheral Device Management in Linux

This guide explains how Linux handles peripheral devices like USB flash drives and printers, and provides step-by-step instructions for interacting with them via both GUI and terminal.

## 1. Understanding Peripheral Device Handling in Linux

### Mounting in Linux
Mounting is the process of linking an external device’s file system to the Linux directory structure, allowing access to its contents.

#### How it Works:
- When a USB flash drive or external storage is connected, Linux detects it as `/dev/sdb`, `/dev/sdc`, etc.
- The device must be mounted to a specific directory (`/mnt/usb`) to access its contents.
- Modern Linux distributions automatically mount USB drives in `/media/username/device-name`.

### Differences Between Linux and Windows
| Feature       | Linux | Windows |
|--------------|-------|---------|
| **Mounting** | Requires explicit mounting via `mount` or automatic mounting through `udev` | Automatically recognized and displayed in File Explorer |
| **File System Support** | Supports EXT4, FAT32, NTFS (via `ntfs-3g`) | Primarily supports FAT32 and NTFS |
| **Printer Drivers** | Uses CUPS (Common Unix Printing System) for managing printers | Uses built-in or vendor-supplied drivers |
| **Terminal Support** | Fully manageable via command line | Mostly GUI-based management |

## 2. Practical Task: Managing USB and Printer in a Virtual Machine

### Copying a File Using GUI:
1. Connect a USB flash drive to the virtual machine.
2. Open the file manager (e.g., Nautilus, Dolphin, or Thunar).
3. Locate the mounted USB drive in the device list.
4. Copy a file from the USB drive to the virtual machine’s local directory.

### Printing a File Using GUI:
1. Connect a printer to the virtual machine.
2. Open **Printer Settings** (`system-config-printer` or **Printers** in system settings).
3. Select the printer or add a new one using CUPS (`http://localhost:631`).
4. Open the file in an application like LibreOffice or a PDF viewer.
5. Send the document to the printer.

### Copying a File Using Terminal:
1. Identify the USB drive:
   ```
   lsblk
   ```
   ![image](https://github.com/user-attachments/assets/6f93a09b-6bb2-4eef-9021-c4cd74d6d674)

2. If not auto-mounted, manually mount the USB:
   ```
   sudo mount /dev/sdb1 /mnt/usb
   ```
3. Copy the file to the local system:
   ```
   cp /mnt/usb/file.txt ~/Documents/
   ```

### Printing a File Using Terminal:
1. Check available printers:
   ```
   lpstat -p -d
   ```
2. Print the file using:
   ```
   lp -d printer_name ~/Documents/file.txt
   ```

### Unmounting the USB Device:
Once finished, safely unmount the USB device:
```
sudo umount /mnt/usb
```
### Unfortunately, I do not have a working printer, I could not perform the interference as required
### Conclusion 
By completing this task, I gained hands-on experience managing external devices in Linux. I learned how mounting works, the differences between Linux and Windows when handling peripherals, and how to copy and print files using both the GUI and terminal. These skills will be useful for troubleshooting and efficiently working with Linux systems in the future.
