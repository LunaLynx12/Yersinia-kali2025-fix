# GNS3 Server Installation with Yersinia on Kali Linux (GUI)

This guide provides step-by-step instructions for installing the GNS3 server with Yersinia support on Kali Linux (GUI mode). Ensure you run all commands as root.

## Prerequisites
- Kali Linux (GUI version)
- Root access
- Internet connection

## Installation Steps

### 1. Remove Existing Yersinia Packages
```bash
apt remove --auto-remove yersinia
apt purge --auto-remove yersinia
```
### 2. Add Kali Archive Keyring
```bash
wget https://archive.kali.org/archive-keyring.gpg -O /usr/share/keyrings/kali-archive-keyring.gpg
```

### 3. Clone Yersinia Repository
```bash
git clone https://github.com/tomac/yersinia.git /opt/yersinia
```

### 4. Install Dependencies
```bash
apt install autoconf libgtk-3-dev libnet1-dev libpcap-dev libgtk2.0-dev -y
```

### 5. Apply Necessary Fixes
Navigate to the Yersinia directory:

```bash
cd /opt/yersinia
```
Replace the original admin.c and admin.h files with the fixed versions from this repository.

### 6. Build and Install Yersinia
```bash
./autogen.sh
./configure --with-gtk
make
make install
```

### 7. Launch Yersinia (GUI Mode)
```bash
yersinia -G
```

## Notes
- Running as root is required for proper functionality
- The GTK flag (--with-gtk) enables the graphical interface
- If you encounter any issues during compilation, verify all dependencies are installed and the fixes are properly applied
