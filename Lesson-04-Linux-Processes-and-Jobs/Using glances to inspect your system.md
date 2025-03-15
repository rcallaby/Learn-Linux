# Using glances to inspect your system

**Glances** is a cross-platform system monitoring tool designed to provide a high-level overview of system performance in real time. It is an excellent alternative to traditional monitoring tools like `top` and `htop`, offering a more detailed and interactive way to observe Linux processes and system metrics.

---

## **1. Installing Glances**
### **On Debian/Ubuntu:**
```bash
sudo apt update && sudo apt install glances -y
```
### **On RHEL/CentOS:**
```bash
sudo dnf install glances -y
```
### **On Arch Linux:**
```bash
sudo pacman -S glances
```
### **Using pip (Universal Method for Latest Version):**
```bash
pip install glances
```

---

## **2. Launching Glances**
Once installed, you can start Glances by simply running:
```bash
glances
```
This will display a dynamic, color-coded dashboard that provides an overview of system resources.

---

## **3. Understanding the Glances Interface**
Glances provides various system details, including:
- **CPU Usage** (per core, load average)
- **Memory Usage** (RAM, Swap)
- **Disk I/O** (read/write speeds, partitions)
- **Network Traffic** (throughput per interface)
- **Processes** (sorted dynamically by resource consumption)
- **Temperature Sensors** (if applicable)
- **Containers & Virtual Machines** (Docker, LXC support)

---

## **4. Common Use Cases for Monitoring Linux Processes and Jobs**

### **4.1 Viewing Running Processes**
The **processes** section of Glances lists active processes along with:
- **PID (Process ID)**
- **CPU usage (%)**
- **Memory consumption**
- **User owning the process**
- **Status (Running, Sleeping, etc.)**

To filter processes dynamically, press:
- **`p`** → Sort processes by CPU usage.
- **`m`** → Sort processes by memory consumption.
- **`i`** → Sort processes by I/O usage.

#### **Tip: Killing a Process**
You can kill a process directly within Glances:
1. Press **`k`** to enter process kill mode.
2. Enter the **PID** of the process to terminate it.

---

### **4.2 Monitoring System Load**
- **CPU usage** is displayed per core, with an overall load percentage.
- The **Load Average** (1m, 5m, 15m) helps determine if the system is overloaded.

#### **Tip: Quick Load Interpretation**
- A load average below `1.0` per core is optimal.
- If the load average exceeds the number of CPU cores, performance may degrade.

---

### **4.3 Checking Memory Usage**
- Glances displays **total, used, and available RAM**.
- Swap usage is also shown, useful for detecting memory exhaustion.

#### **Tip: Reducing Swap Usage**
If swap is being overused, consider:
```bash
sudo swapoff -a && sudo swapon -a
```
or identifying memory-heavy processes using **`m`** in Glances.

---

### **4.4 Monitoring Disk I/O**
- Glances shows read/write speeds of storage devices.
- Helps in diagnosing **high I/O wait times**.

#### **Tip: Identify Disk Bottlenecks**
- If disk I/O is consistently high, check specific processes using:
```bash
iotop
```
- For detailed disk health analysis:
```bash
smartctl -a /dev/sdX
```

---

### **4.5 Network Monitoring**
- Glances displays live network traffic (incoming/outgoing) per interface.
- Packet errors or high latency indicate networking issues.

#### **Tip: Analyzing Network Usage**
If network usage spikes unexpectedly, use:
```bash
sudo netstat -tulnp
```
or
```bash
sudo lsof -i
```
to find processes consuming bandwidth.

---

## **5. Running Glances in Web Mode**
Glances can be accessed remotely through a web interface:

### **Start the Web UI**
```bash
glances -w
```
Then, access it via:
```bash
http://<server-ip>:61208
```

---

## **6. Remote Monitoring with Glances**
You can monitor another system over SSH by running Glances in server mode:

### **On the remote system (server)**
```bash
glances -s
```
### **On the local system (client)**
```bash
glances -c <server-ip>
```

---

## **7. Exporting System Metrics**
Glances can export real-time metrics to various formats:
- JSON (`--export json`)
- CSV (`--export csv`)
- InfluxDB for long-term monitoring (`--export influxdb`)

Example:
```bash
glances --export json
```

---

## **8. Useful Keyboard Shortcuts in Glances**
| Key  | Function |
|------|----------|
| `q`  | Quit Glances |
| `p`  | Sort processes by CPU usage |
| `m`  | Sort processes by memory usage |
| `i`  | Sort processes by I/O usage |
| `k`  | Kill a process |
| `1`  | Show per-core CPU stats |
| `d`  | Show disk I/O details |
| `n`  | Show network traffic details |
| `f`  | Enable process filtering |
| `/`  | Search for a specific process |
| `h`  | Show help menu |

---

## **Conclusion**
Glances is an incredibly powerful tool for **monitoring system performance and managing processes efficiently**. It provides **real-time insights** into CPU, memory, disk, and network usage in an intuitive way. Whether you're troubleshooting system performance, identifying resource-heavy processes, or remotely monitoring a server, Glances is an essential tool for any Linux user.