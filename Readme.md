# Embedded Linux Essentials

A collection of topics related to (Embedded) Linux that a professional in this field should be familiar with.

---

The general chapters and main topics associated to the individual subchapters are meant to represent the
broad knowledge that can be _expected from any Embedded Linux professional_.
For some topics, detailed knowledge could be _expected from more advanced professionals_ - the corresponding
sections can be expanded with a click.

Beyond this point, there is only a rough guidance on what level of detail could be expected in relation to a
professional's experience grade, represented by the level of indentation.


## 1 Linux Fundamentals
General concepts & properties of any Linux based system (including desktop or server distributions).
A solid foundation here allows to _reuse as many OS mechanisms as possible_ and to _avoid building conceptually broken software_.

### 1.1 Principles & Concepts

<details><summary><b>The Linux Kernel</b></br>

_How the kernel operates and interacts with the applications on the system._
</summary>

* scheduling
* signals
</details>

<details><summary><b>Kernel- & Userspace</b></br>

_How the two separate runtime contexts differ and interact._
</summary>

* system calls
</details>

<details><summary><b>Everything is a File</b></br>

_How the system's entities are represented to the user._
</summary>

* file descriptors
* symlinks, hardlinks
</details>

<details><summary><b>Processes & Threads</b></br>

_How application logic is executed._
</summary>
</details>

<details><summary><b>Networking & Protocols</b></br>

_How to interconnect multiple devices in a network._
</summary>

* ISO/OSI protocol layers and common protocols (IPv4, IPv6, TCP, UDP, IEEE 802.11)
* Configuring network interfaces in Linux (netctl, NetworkManager, ConnMan, iwd, wpa_supplicant, systemd-networkd, ...)
* Troubleshooting (`ping`, `traceroute`, `ssh`, `netstat`, `nmap`, `dig`, Wireshark)
</details>

<details><summary><b>User & Access Management</b></br>

_How access to and ownership of data and execution logic is handled._
</summary>

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

* rootfs
* `chroot`
</details>

<details><summary><b>Block Device Filesystems</b></br>

_How to choose and work with the filesystems on disc._
</summary>

* types (`ext4`, `squashfs`, `ubifs`)
* utilities
  * `mkfs`
  * `fsck`
* mounting (`mount`, `umount`)
</details>

<details><summary><b>Special Filesystems</b></br>

_How to use the filesystems exposing kernel features or virtually extending the system._
</summary>

* `procfs`
* `sysfs`
* `tmpfs`
* `overlayfs`
</details>

### 1.3 Partitioning

<details><summary><b>Partition Table</b></br>

_How to define and interpret the system's partition table._
</summary>

* formats (`msdos`, `gpt`)
* utilities (`parted`)
</details>

<details><summary><b>Mounting</b></br>

_How to add filesystems to the rootfs_
.</summary>

* formats (`msdos`, `gpt`)
* utilities (`parted`)
</details>

### 1.4 I/O

<details><summary><b>Event Handling</b></br>

_How to detect and react on (file) events._
</summary>

* `ppoll`, `select`
</details>

<details><summary><b>Interprocess Communication (IPC)</b></br>

_How to use built-in features to communicate between processes._
</summary>

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

* `systemd`
  * units
  * overrides
  * utilities (`systemctl`, `journalctl`, `systemd-run`, ...)
* `cgroups`
</details>

<details><summary><b>Monitoring</b></br>

_How to monitor applications on the system._
</summary>

* Software watchdog (`systemd_notify`)
</details>

### 1.6 External Devices

<details><summary><b>Device Rules</b></br>

_How to integrate external devices._
</summary>

* `udev`
</details>

---

## 2 Embedded Specifics
Topics mostly relating to embedded devices and their specific product use case.

### 2.1 Board Support

<details><summary><b>Bootloader</b></br>

_How to interact with and/or extend the behavior of the bootloader._
</summary>

* `uboot`
  * Repository structure
  * Configuring / patching uboot
  * uboot environments
  * `fw_*env` tools
* `grub`
  * grub.env
* (`efi`)
</details>


<details><summary><b>Device Trees</b></br>

_How to enable hardware features in the operating system._
</summary>
</details>

<details><summary><b>Drivers</b></br>

_How to use (or implement) drivers for extended system features._
</summary>
</details>

<details><summary><b>Peripherals</b></br>

_How to interact with peripherals on the hardware board._
</summary>

* HSM / TPM
* Flash memory
  * eMMC
  * NAND/NOR
</details>

### 2.2 Libraries & Tools

<details><summary><b>Constrained Devices Support</b></br>

_How to use the reduced feature set of embedded-specific tools._
</summary>

* `busybox`
</details>

<details><summary><b>Cryptography</b></br>

_How to implement security features with existing libraries._
</summary>

* `openssl`
* `libsodium`
* `wolfssl`
* Mbed TLS
</details>

<details><summary><b>Binaries</b></br>

_How binaries are assembled in Linux._
</summary>

* static & dynamic linking
* `RPATH`, `LD_PRELOAD` and other environment variables
* cross-compilation, canadian cross concept
* troubleshooting (`ldd`, `readelf`, `objdump`, `file`)
</details>

---

## 3 Working with Linux
Knowledge helpful when working with Linux-based systems.

### 3.1 Utilities

<details><summary><b>File operations</b></br>

_How to use the built-in tools._
</summary>

* `ls`, `cat`, `head`, `tail`, `less`, `echo`
* `grep`, `awk`
</details>

<details><summary><b>Editors</b></br>

_How to view and edit files on the device._
</summary>

* `vi` / `vim`
* `nano`
</details>

<details><summary><b>Scripting</b></br>

_How to implement complex logic using the native command line._
</summary>

* sh / bash
* zsh, hsh, ...
</details>

<details><summary><b>Process Management</b></br>

_How to use the built-in process related tools._
</summary>

* `fuser`
* `kill`
</details>

<details><summary><b>Logging</b></br>

_How to leverage built-in logging features._
</summary>

* `dmesg`
* syslog (`logger`)
* `journald` 
</details>

<details><summary><b>System Inspection</b></br>

_How to gather information about the operating system and applications._
</summary>

* Disk usage (`df`, `du`)
* Runtime stats (`ps`, `top`)
</details>

<details><summary><b>Debugging</b></br>

_How to analyse the system in case of unexpected behavior._
</summary>

* `coredump`
* `kdump`
</details>

---

## 4 Use Case Building Blocks
Partial solutions or technical approaches for use cases commonly seen in embedded Linux products.

### 4.1 Build Systems

<details><summary><b>Yocto</b></br>

_How the package-based image build system works and when to choose it._
</summary>
</details>

<details><summary><b>Buildroot</b></br>

_How the distribution build system works and when to choose it._
</summary>
</details>

### 4.2 Application Management

<details><summary><b>Package Managers</b></br>

_How to manage static application versioning and dependencies on the device._
</summary>

* `dpkg` / `apt`
* `ipkg` / `opkg`
* `dnf` / `rpm`
</details>

### 4.3 Update Frameworks

<details><summary><b>Update Clients</b></br>

_How to handle updates on the device._
</summary>

* `rauc`
* `swupdate`
</details>

<details><summary><b>Incremental Update Support</b></br>

_How to reduce update transmission bandwidth._
</summary>

* `casync`
* `OSTree`
</details>

### 4.4 System Hardening

<details><summary><b>Read-only Rootfs</b></br>

_How to reduce the number of writes to the rootfs and protect it against undesired manipulation._
</summary>

* systemd requirements
* pre-init & overlays
</details>

### 4.5 Security

**TODO**: Extend security section.
