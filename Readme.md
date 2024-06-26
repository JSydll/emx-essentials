# Embedded Linux Essentials

A collection of topics related to (Embedded) Linux that a professional in this field should be familiar with.

---

The general chapters and main topics associated to the individual subchapters are meant to represent the
broad knowledge that can be _expected from any Embedded Linux professional_.
For some topics, detailed knowledge could be _expected from more advanced professionals_ - the corresponding
sections can be expanded with a click.

Beyond this point, there is only a rough guidance on what level of detail could be expected in relation to a
professional's experience grade, represented by the level of indentation.

**Contents**

* [Linux Fundamentals](#1-linux-fundamentals)
  - [Principles & Concepts](#11-principles--concepts)
  - [Filesystem](#12-filesystem)
  - [Partitioning](#13-partitioning)
  - [Processing & Communication](#14-processing--communication)
  - [System Management](#15-system-management)
  - [External Devices](#16-external-devices)
  - [Networking](#17-networking)

* [Embedded Specifics](#2-embedded-specifics)
  - [Board Support](#21-board-support)
  - [Libraries & Tools](#22-libraries--tools)

* [Working with Linux](#3-working-with-linux)

* [Building Blocks](#4-building-blocks)
  - [Build Systems](#41-build-systems)
  - [Application Management](#42-application-management)
  - [Update Frameworks](#43-update-frameworks)
  - [Robustness](#44-robustness)
  - [Security](#45-security)

Some helpful learning resources are attached to the individual topics in the respective details section.

---


## 1 Linux Fundamentals
General concepts & properties of any Linux based system (including desktop or server distributions).
A solid foundation here allows to _reuse as many OS mechanisms as possible_ and to _avoid building conceptually broken software_.

_Resources_:
- [M. Kerrisk - The Linux Programming Interface](https://man7.org/tlpi/)

### 1.1 Principles & Concepts

<details><summary><b>The Linux Kernel</b></br>

_How the kernel operates and interacts with the applications on the system._
</summary>

_Subtopics_:
* scheduling
* signals
</details>

<details><summary><b>Kernel- & Userspace</b></br>

_How the two separate runtime contexts differ and interact._
</summary>

_Subtopics_:
* system calls
</details>

<details><summary><b>Everything is a File</b></br>

_How the system's entities are represented to the user._
</summary>

_Subtopics_:
* file descriptors
* symlinks, hardlinks
</details>

<details><summary><b>Processes & Threads</b></br>

_How application logic is executed._
</summary>
</details>

<details><summary><b>User & Access Management</b></br>

_How access to and ownership of data and execution logic is handled._
</summary>

_Subtopics_:
* Access Control Lists (ACL)
* Passwords & keys
* Real & effective IDs
* Users (`id`, `whoami`, `sudo`, `su`)
* Ownership (`chown`, `chmod`)
</details>

<details><summary><b>System Startup & Shutdown</b></br>

_How the system enters & quits operation._
</summary>

From 1st stage to 2nd stage bootloader,
kernel (+ initramfs) and finally the
system manager (systemd) and userspace.
</details>

### 1.2 Filesystem

<details><summary><b>System Root</b></br>

_How the filesystem is structured, visible and protected against manipulation._
 </summary>

_Subtopics_:
* rootfs
* `chroot`
</details>

<details><summary><b>Block Device Filesystems</b></br>

_How to choose and work with the filesystems on disc._
</summary>

_Subtopics_:
* types (`ext4`, `squashfs`, `ubifs`)
* utilities
  * `mkfs`
  * `fsck`
* mounting (`mount`, `umount`)
</details>

<details><summary><b>Special Filesystems</b></br>

_How to use the filesystems exposing kernel features or virtually extending the system._
</summary>

_Subtopics_:
* `procfs`
* `sysfs`
* `tmpfs`
* `overlayfs`
</details>

### 1.3 Partitioning

<details><summary><b>Partition Table</b></br>

_How to define and interpret the system's partition table._
</summary>

_Subtopics_:
* formats (`msdos`, `gpt`)
* utilities (`parted`)
</details>

<details><summary><b>Mounting</b></br>

_How to add filesystems to the rootfs_.
</summary>

_Subtopics_:
* formats (`msdos`, `gpt`)
* utilities (`parted`)
</details>

### 1.4 Processing & Communication

<details><summary><b>Event Handling</b></br>

_How to detect and react on (file) events._
</summary>

_Subtopics_:
* `ppoll`, `select`
</details>

<details><summary><b>Interprocess Communication (IPC)</b></br>

_How to use built-in features to communicate between processes._
</summary>

_Subtopics_:
* sockets
* pipes
* shared memory API (`shm_open`, `mmap`, ...)
* message queues
* signals
</details>

### 1.5 System Management

<details><summary><b>Orchestration</b></br>

_How to manage dependencies, resources and the lifetime of applications on the system._
</summary>

_Subtopics_:
* `systemd`
  * units
  * overrides
  * utilities (`systemctl`, `journalctl`, `systemd-run`, `systemd-analyze`, ...)
* `cgroups`
</details>

<details><summary><b>Monitoring</b></br>

_How to monitor applications on the system._
</summary>

_Subtopics_:
* Software watchdog (`systemd_notify`)
</details>

### 1.6 External Devices

<details><summary><b>Device Rules</b></br>

_How to integrate external devices._
</summary>

_Subtopics_:
* `udev`
</details>

### 1.7 Networking

<details><summary><b>Networking & Protocols</b></br>

_How to interconnect multiple devices in a network._
</summary>

_Subtopics_:
* ISO/OSI protocol layers and common protocols (IPv4, IPv6, TCP, UDP, IEEE 802.11)
* Configuring network interfaces in Linux (netctl, NetworkManager, ConnMan, iwd, wpa_supplicant, systemd-networkd, ...)
* Troubleshooting (`ping`, `traceroute`, `ssh`, `netstat`, `nmap`, `dig`, Wireshark)
</details>

---

## 2 Embedded Specifics
Topics mostly relating to embedded devices and their specific product use case.

_General resources_:
- [Bootlin Embedded Linux course (info & material)](https://bootlin.com/training/embedded-linux/)

### 2.1 Board Support

<details><summary><b>Bootloader</b></br>

_How to interact with and/or extend the behavior of the bootloader._
</summary>

_Subtopics_:
* `U-Boot`
  * Repository structure
  * Configuring / patching u-boot
  * u-boot environments
  * `fw_*env` tools
* `barebox`
* `grub`
  * grub.env
* (`efi`)
</details>


<details><summary><b>Device Trees</b></br>

_How to enable hardware features in the operating system._
</summary>

_Resources_:
- [Introduction to Device Trees [Toradex] (Youtube)](https://www.youtube.com/watch?v=Nz6aBffv-Ek)
</details>

<details><summary><b>Drivers</b></br>

_How to use (or implement) drivers for extended system features._
</summary>

_Resources_:
- [Understanding the Structure of a Linux Kernel Device Driver [Toradex] (Youtube)](https://www.youtube.com/watch?v=pIUTaMKq0Xc)
</details>

<details><summary><b>Peripherals</b></br>

_How to interact with peripherals on the hardware board._
</summary>

_Subtopics_:
* HSM / TPM
* Flash memory
  * eMMC
  * NAND/NOR
</details>

### 2.2 Libraries & Tools

<details><summary><b>Constrained Devices Support</b></br>

_How to use the reduced feature set of embedded-specific tools._
</summary>

_Subtopics_:
* `busybox`
</details>

<details><summary><b>Cryptography</b></br>

_How to implement security features with existing libraries._
</summary>

_Subtopics_:
* `openssl`
* `libsodium`
* `wolfssl`
* Mbed TLS
</details>

<details><summary><b>Binaries</b></br>

_How binaries are assembled in Linux._
</summary>

_Subtopics_:
* static & dynamic linking
* `RPATH`, `LD_PRELOAD` and other environment variables
* cross-compilation, canadian cross concept
* troubleshooting (`ldd`, `readelf`, `objdump`, `file`)
</details>

<details><summary><b>Flashing tools</b></br>

_How to deploy software on the actual hardware._
</summary>

* [uuu / mfgtools (by NXP)](https://github.com/nxp-imx/mfgtools)
* [snagboot / snagflash (by Bootlin)](https://github.com/bootlin/snagboot)
</details>

<details><summary><b>System testing</b></br>

_What frameworks to use when testing with hardware-in-the-loop._
</summary>

* [labgrid (by Pengutronix)](https://github.com/labgrid-project/labgrid)
</details>

---

## 3 Working with Linux
Knowledge helpful when working with Linux-based systems.

<details><summary><b>File operations</b></br>

_How to use the built-in tools._
</summary>

_Subtopics_:
* `ls`, `cat`, `head`, `tail`, `less`, `echo`
* `grep`, `awk`
</details>

<details><summary><b>Editors</b></br>

_How to view and edit files on the device._
</summary>

_Subtopics_:
* `vi` / `vim`
* `nano`
</details>

<details><summary><b>Scripting</b></br>

_How to implement complex logic using the native command line._
</summary>

_Subtopics_:
* sh / bash
* zsh, hsh, ...
* interoperability (e.g. avoiding bashisms)
</details>

<details><summary><b>Process Management</b></br>

_How to use the built-in process related tools._
</summary>

_Subtopics_:
* `fuser`, `lsof`
* `kill`
</details>

<details><summary><b>Logging</b></br>

_How to leverage built-in logging features._
</summary>

_Subtopics_:
* `dmesg`
* syslog (`logger`)
* `journald` 
</details>

<details><summary><b>Application Analytics<b></br>

_How to get performance metrics, profiles and call graphs for applications._
</summary>

_Subtopics_:
* `perf`, `gprof`, [`hotspot`](https://github.com/KDAB/hotspot)
* `valgrind`, `kcachegrind`, ...
</details>

<details><summary><b>System Inspection</b></br>

_How to gather information about the operating system and applications._
</summary>

_Subtopics_:
* Disk usage (`df`, `du`)
* Runtime stats (`ps`, `top`)
</details>

<details><summary><b>Debugging</b></br>

_How to analyse the system in case of unexpected behavior._
</summary>

_Subtopics_:
* `coredump`
* `kdump`
</details>

---

## 4 Building Blocks
Partial solutions or technical approaches for use cases commonly seen in embedded Linux products.

### 4.1 Build Systems

<details><summary><b>Yocto</b></br>

_How the package-based image build system works and when to choose it._
</summary>

_Resources_:
- [Official Yocto documentation](https://docs.yoctoproject.org/)
- [Yocto crash course by Bootlin](https://bootlin.com/doc/training/yocto/yocto-slides.pdf)
- [Mender.io's collection of Yocto tutorials](https://hub.mender.io/c/tutorials/yocto-project/19)
</details>

<details><summary><b>Buildroot</b></br>

_How the distribution build system works and when to choose it._
</summary>
</details>

### 4.2 Application Management

<details><summary><b>Package Managers</b></br>

_How to manage static application versioning and dependencies on the device._
</summary>

_Subtopics_:
* `dpkg` / `apt`
* `ipkg` / `opkg`
* `dnf` / `rpm`
</details>

### 4.3 Update Frameworks

<details><summary><b>Update Clients</b></br>

_How to handle updates on the device._
</summary>

_Subtopics_:
* `rauc`
* `swupdate`

_Resources_:
- Introductions [here](https://www.pengutronix.de/de/blog/2019-08-16-rauc_maintenance.html), [here](https://mkrak.org/2018/01/10/updating-embedded-linux-devices-part1/) or [here](https://sbabic.github.io/swupdate/scenarios.html)
- [RAUC documentation](https://www.rauc.io/)
- [SWUpdate documentation](https://sbabic.github.io/swupdate/swupdate.html)
</details>

<details><summary><b>Incremental Update Support</b></br>

_How to reduce update transmission bandwidth._
</summary>

_Subtopics_:
* `casync`
* `OSTree`
</details>

### 4.4 Robustness

<details><summary><b>Read-only Rootfs</b></br>

_How to reduce the number of writes to the rootfs and protect it against undesired manipulation._
</summary>

_Subtopics_:
* systemd requirements
* pre-init & overlays

_Resources_:
- [Pre-init for /etc overlay (Yocto)](https://git.yoctoproject.org/poky/tree/meta/classes-recipe/overlayfs-etc.bbclass)
</details>

### 4.5 Security

**TODO**: Extend security section.
