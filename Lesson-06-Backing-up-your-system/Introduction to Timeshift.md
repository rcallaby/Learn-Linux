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

### Step 2: Configure Timeshift

Once Timeshift is installed, you’ll need to configure it to define backup schedules, select snapshot types, and manage included or excluded files. Timeshift can be configured using either the **Graphical User Interface (GUI)** or the **Command Line Interface (CLI)**. This guide covers both approaches in detail.

---

### **Accessing Timeshift**

#### **Graphical Interface (GUI)**

To launch the Timeshift GUI:

* **Via Application Menu**: Open your system’s application launcher and search for **Timeshift**.
* **Via Terminal**:

  ```bash
  sudo timeshift-gtk
  ```

> Running Timeshift with `sudo` is required to access system-level files.

---

### **Timeshift GUI Overview**

Once the GUI is launched, you'll see a setup wizard the first time you open it. This guides you through selecting the snapshot type, destination, schedule, and filters.

After setup, the main interface has **four primary tabs**:

#### **1. Snapshot Tab**

This is the default tab and displays a list of existing snapshots.

* **Create Snapshot**:
  Click **Create** to manually generate a new snapshot. Timeshift supports two snapshot types:

  * **System** (default): Backs up system files and settings (e.g., `/etc`, `/usr`, `/var`, but excludes `/home`).
  * **System + Home**: Includes user files in `/home`, useful for full system recovery.

* **Browse/Restore/Delete**:
  Use the **Browse** button to explore files in a snapshot (mounted read-only). **Restore** reverts your system to the selected state. **Delete** removes old or unnecessary snapshots.

#### **2. Rsync Tab**

Only visible if you selected **Rsync** as the snapshot method during setup.

* Allows configuration of:

  * **Backup device** and location
  * **Include/Exclude rules** for directories
  * **Snapshot schedule** (hourly, daily, weekly, etc.)

> Timeshift does **not** back up non-system partitions (e.g., `/mnt`, `/media`) by default. Use the filters to adjust this.

#### **3. Settings Tab**

This is where you fine-tune Timeshift’s behavior.

* **Schedule**:
  Enable and configure automatic snapshot frequencies. You can enable:

  * Hourly (max: 6)
  * Daily (max: 5)
  * Weekly (max: 3)
  * Monthly (max: 2)
  * Boot (max: 3)

* **Snapshot Levels**:
  Limit how many snapshots of each type Timeshift retains. Oldest ones are deleted automatically when limits are reached.

* **Users**:
  By default, Timeshift excludes user home directories. Enable inclusion explicitly here if needed.

* **Filters**:
  Add patterns to **include or exclude specific files/directories** from snapshots. Use this to exclude large media folders, caches, or temporary directories.

* **Location**:
  Set the destination for storing snapshots. This should ideally be a separate partition or an external drive (formatted with a Linux-compatible filesystem like ext4).

#### **4. Help Tab**

Provides links to:

* Official Timeshift documentation
* Community support forums
* Bug report submissions

---

### **Timeshift CLI (Command-Line Interface)**

For advanced users or remote systems, Timeshift can be used via CLI.

#### **Launch CLI Interface**:

```bash
sudo timeshift
```

#### **Common CLI Commands**

* **Create a Snapshot with a Custom Comment**:

  ```bash
  sudo timeshift --create --comments "My Custom Snapshot"
  ```

* **List Existing Snapshots**:

  ```bash
  sudo timeshift --list
  ```

* **Delete a Specific Snapshot**:

  ```bash
  sudo timeshift --delete --snapshot '2024-06-18_10-00-00'
  ```

* **Restore from a Snapshot**:

  ```bash
  sudo timeshift --restore
  ```

  > The CLI will walk you through the restoration steps interactively. Ensure all work is saved before proceeding.

* **Create a Snapshot Using an External Device**:

  ```bash
  sudo timeshift --create --rsync --backup-device /dev/sdb1 --backup-path /media/external_drive
  ```

  > Make sure the external drive is mounted and writable.

---

### **Best Practices and Notes**

* **Use a Dedicated Partition or Drive**: Avoid saving snapshots on the same partition as your root filesystem to prevent filling up disk space during failure recovery.
* **Regularly Check Your Snapshot Schedule**: Timeshift doesn’t automatically notify you of backup failures unless integrated with cron or email alerts.
* **Automate Snapshot Pruning**: Set retention policies under the "Settings" tab to avoid manual cleanup.
* **Timeshift Is Not a File-by-File Backup Tool**: It's for system recovery. For user file backup, use tools like `rsync`, `Deja Dup`, or `BorgBackup`.

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