# IT Infrastructure Simulation Project

Welcome to my enterprise IT and security Simulation! This project is a documentation of my journey building a corporate IT environment from scratch. Designed to simulate real-world infrastructure, this lab serves as a dedicated space for practicing system administration, security engineering, and network deployment.

## Project Overview

The goal of this simulation is to bridge the gap between theory and practice by deploying a fully functional Active Directory environment, configuring network security policies, and managing endpoints just like a modern enterprise.

---

## Phase 1: Laying the Foundation (Hyper-V Setup)

Before building the virtual domain, I needed a hypervisor to host it. I opted for Microsoft's native **Hyper-V** to manage the virtualization layer.

### 1.1 Unlocking Hyper-V
To get started, the built-in virtualization capabilities on the host machine needed to be awakened:
1. Navigated to **Control Panel > Programs > Programs and Features**.
2. Clicked on **Turn Windows features on or off**.
3. Checked the box for **Hyper-V**, hit OK, and rebooted the host machine to apply changes.

### 1.2 Architecting the Virtual Network
A lab is no good if the machines can't communicate.
1. Opened **Hyper-V Manager**.
2. Launched the **Virtual Switch Manager** from the Actions pane.
3. Created a new **External virtual switch** linked to my primary network adapter.
   * *Purpose:* This acts as the bridge, allowing VMs to securely access the physical network and the internet.

---

## Phase 2: Forging the Servers

With the hypervisor ready, it was time to establish the backbone of the infrastructure.

### 2.1 The Brains of the Operation: Domain Controller (DC01)
Every corporate network needs a central source of truth.
* **VM Name:** `DC01`
* **OS:** Windows Server 2022 (Desktop Experience)
* **Generation:** Gen 1
* **Memory:** 4096 MB (Dynamic Memory Enabled)
* **Storage:** 2TB Virtual Hard Disk
* **Network:** Connected to the External Switch created in Phase 1.

### 2.2 The Supporting Pillar: Secondary Server (SV02)
Redundancy and separation of duties are key.
* **VM Name:** `SV02`
* **OS:** Windows Server 2022
* **Configuration:** Mirrored the specs of DC01.
* **Purpose:** Ready to host secondary services, file shares, or act as a target machine for implementation testing.

---

##  Phase 3: Populating the Floor (Client VMs)

To simulate a real network of employees, I created a fleet of Windows 10 client machines.
My make believe company is CHOIYONTECH

### 3.1 Spinning Up the Endpoints
* **VM Names:** `CHOIYONTECH-PC01`, `CHOIYONTECH-PC02`, `CHOIYONTECH-PC03`, `CHOIYONTECH-PC04`
* **OS:** Windows 10
* **Memory:** 1024 MB each
* **Setup:**
  * Ran the Hyper-V creation wizard four separate times.
  * Mounted the standard Windows 10 `.iso` as the boot disk.
  * Pushed them through the standard installation process.

---

### Next Steps (in progress)
* [ ] Domain Configuration & Active Directory Integration
* [ ] DHCP & DNS Setup
* [ ] User & Group Policy Management
* [ ] Security Hardening
