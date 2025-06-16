# Introduction to Timeshift

In this tutorial, I will guide you through using the Linux backup utility called Timeshift. Timeshift is a powerful and easy-to-use backup tool that can help you create snapshots of your Linux system, allowing you to quickly restore your system to a previous state if something goes wrong. This tutorial will cover the basics of Timeshift, including how to install it, create backups, and restore your system from a backup.

### Step 1: Install Timeshift
The first step is to install Timeshift on your Linux system. Timeshift is available in most Linux distributions, including Ubuntu, Debian, Fedora, and Arch Linux. You can install it using the following commands:

## Overview

**Timeshift** is maintained here:
🔗 GitHub: [https://github.com/teejee2008/timeshift](https://github.com/teejee2008/timeshift)
It supports both **RSYNC** and **BTRFS** snapshot methods.

> **Minimum Requirement**: Root (sudo) privileges.

---

## Installation Methods by Distribution



### **Ubuntu / Linux Mint / Pop!\_OS / Elementary OS**

(Ubuntu-based distributions)

#### Steps:

1. **Update package lists**:

   ```bash
   sudo apt update
   ```

2. **Install Timeshift**:

   ```bash
   sudo apt install timeshift
   ```

3. **Verify Installation**:

   ```bash
   timeshift --version
   ```

#### Notes:

* In Ubuntu 22.04 and later, Timeshift is in the **universe** repo.
* If it fails to install, ensure `universe` is enabled:

  ```bash
  sudo add-apt-repository universe
  sudo apt update
  ```

---

### **Debian (10/Buster, 11/Bullseye, etc.)**

#### Steps:

1. **Add the required dependencies**:

   ```bash
   sudo apt update
   sudo apt install software-properties-common
   ```

2. **Enable backports if on older releases** (for newer Timeshift versions):

   ```bash
   echo "deb http://deb.debian.org/debian bullseye-backports main" | sudo tee /etc/apt/sources.list.d/backports.list
   sudo apt update
   ```

3. **Install Timeshift**:

   ```bash
   sudo apt install timeshift
   ```

4. **Verify**:

   ```bash
   timeshift --help
   ```

---

### **Fedora (Workstation or Server)**

Timeshift is available via **RPM Fusion Free repository**.

#### Steps:

1. **Enable RPM Fusion Free**:

   ```bash
   sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
   ```

2. **Install Timeshift**:

   ```bash
   sudo dnf install timeshift
   ```

3. **Verify**:

   ```bash
   timeshift --version
   ```

---

### **CentOS / RHEL / AlmaLinux / Rocky Linux**

Timeshift is not in official repos. Use a **Flatpak** or build from source.

#### Option 1: Use Flatpak (Recommended for stability)

1. **Install Flatpak (if not already installed)**:

   ```bash
   sudo dnf install flatpak
   ```

2. **Add Flathub repository**:

   ```bash
   flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
   ```

3. **Install Timeshift**:

   ```bash
   flatpak install flathub com.github.timeshift
   ```

4. **Run Timeshift**:

   ```bash
   flatpak run com.github.timeshift
   ```

---

### **Arch Linux / Manjaro / EndeavourOS / Garuda**

Timeshift is available in the **official Arch repositories**.

#### Steps:

1. **Update system**:

   ```bash
   sudo pacman -Syu
   ```

2. **Install Timeshift**:

   ```bash
   sudo pacman -S timeshift
   ```

3. **Verify**:

   ```bash
   timeshift --version
   ```

---

### **openSUSE (Leap / Tumbleweed)**

Timeshift may not be in the official repos, but is available in OBS (openSUSE Build Service).

#### Option 1: Install via OBS (Open Build Service)

1. **Enable repository (Leap 15.5 example)**:

   ```bash
   sudo zypper ar https://download.opensuse.org/repositories/system:/timeshift/openSUSE_Leap_15.5/ timeshift-repo
   sudo zypper refresh
   ```

2. **Install Timeshift**:

   ```bash
   sudo zypper install timeshift
   ```

---

## Post-Installation Setup (Universal)

1. **Run the GUI or CLI Wizard**:

   ```bash
   sudo timeshift-gtk  # GUI
   sudo timeshift --create  # CLI
   ```

2. **Select Snapshot Type**:

   * Use **RSYNC** for most filesystems.
   * Use **BTRFS** for native BTRFS volumes (with subvolume support).

3. **Schedule Snapshots** (CLI example):

   ```bash
   sudo timeshift --schedule-daily --count 5
   ```

4. **Create a Snapshot (Manual)**:

   ```bash
   sudo timeshift --create --comments "Initial Backup" --tags D
   ```

---

## 🧪 Verify Timeshift Works

Check that snapshots are created under:

```bash
sudo timeshift --list
```

---

## 📚 Trusted References

* Official GitHub: [https://github.com/teejee2008/timeshift](https://github.com/teejee2008/timeshift)
* Arch Wiki: [https://wiki.archlinux.org/title/Timeshift](https://wiki.archlinux.org/title/Timeshift)
* RPM Fusion: [https://rpmfusion.org/](https://rpmfusion.org/)
* Debian Wiki: [https://wiki.debian.org/](https://wiki.debian.org/)
* Flathub: [https://flathub.org/apps/com.github.timeshift](https://flathub.org/apps/com.github.timeshift)
* Ubuntu Packages: [https://packages.ubuntu.com/search?keywords=timeshift](https://packages.ubuntu.com/search?keywords=timeshift)



### Step 2: Configure Timeshift
Once Timeshift is installed, you need to configure it to set up backup schedules and select which directories and files to backup. The configuration is done through the Timeshift GUI or the Timeshift command-line interface (CLI).

Timeshift GUI
To access the Timeshift GUI, open your system's application launcher and search for Timeshift. Alternatively, you can launch it from the command line using the following command:

```
sudo timeshift-gtk
```
Once the Timeshift GUI is open, you will see the main window with four tabs: Snapshot, Rsync, Settings, and Help.

#### Snapshot Tab
On the Snapshot tab, you can create, browse, and delete snapshots of your system. To create a new snapshot, click the "Create" button and select the type of snapshot you want to create (system or home directory). You can also set the snapshot location, schedule, and exclude specific directories or files.

#### Rsync Tab
On the Rsync tab, you can create and manage backups using the rsync backup method. This method allows you to back up your files and directories to a remote location, such as an external hard drive or a remote server. You can set up a schedule and exclude specific directories or files.

#### Settings Tab
On the Settings tab, you can configure advanced settings for Timeshift, such as the number of snapshots to keep, the snapshot location, and the backup method. You can also enable notifications and set up email alerts.

#### Help Tab
On the Help tab, you can access the Timeshift documentation, submit bug reports, and get help from the Timeshift community.

#### Timeshift CLI
If you prefer to use the command line, you can configure Timeshift using the Timeshift CLI. To access the CLI, open a terminal and type the following command:

```
sudo timeshift
```

To create a new snapshot and set a custom name:
```
sudo timeshift --create --comment "My Custom Snapshot"
```

To list all snapshots:
```
sudo timeshift --list
```

To delete a snapshot:

```
sudo timeshift --delete [snapshot name or ID]
```
To restore your system from a snapshot:
```
sudo timeshift --restore [snapshot name or ID]
```
To create a snapshot using the Rsync backup method:

```
sudo timeshift --create --backup-device /dev/sdb1 --backup-path /media/external_drive --rsync
```
### Step 3: Create a Backup
Now that Timeshift is configured, you can create your first backup

To create a backup using Timeshift, follow these steps:

+ Open the Timeshift GUI or CLI.
+ Click the "Create" button or run the sudo timeshift --create command.
+ Select the type of snapshot you want to create (system or home directory).
+ Set the snapshot location, schedule, and exclude specific directories or files if desired.
+ Click the "Create" button or press enter to start the backup process.
+ The backup process may take some time depending on the size of your system and the type of backup method you selected.

Once the backup is complete, you will see the snapshot listed in the Timeshift GUI or CLI. You can browse the snapshot to see what files and directories were backed up, or delete the snapshot if it is no longer needed.

### Step 4: Restore Your System
If something goes wrong with your Linux system, such as a software or hardware failure, you can use Timeshift to restore your system to a previous state. To restore your system using Timeshift, follow these steps:

+ Open the Timeshift GUI or CLI.
+ Select the snapshot you want to restore from the list.
+ Click the "Restore" button or run the sudo timeshift --restore command.
+ Select the restore location (original or custom).
+ Click the "Restore" button or press enter to start the restore process.
+ The restore process may take some time depending on the size of the snapshot and the type of backup method used. Once the restore is complete, your system will be reverted to the state it was in when the snapshot was taken.


# Conclusion
Timeshift is a powerful backup tool that can help you protect your Linux system from unexpected failures or issues. By creating regular backups using Timeshift, you can quickly restore your system to a previous state and get back to work without losing any data or settings. Whether you prefer to use the GUI or the CLI, Timeshift is a versatile and reliable backup solution for any Linux user.