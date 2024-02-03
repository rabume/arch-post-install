# 🐧 arch-post-install

personal arch post install script for a base arch linux installation

## ✨What does it do?

The script installs yay and all the packages in the [packages.csv](packages.csv) file.

## 📦 Installation

1. **Get the latest arch iso**

   - Flash it to a USB
   - Boot from USB
   - If you want to install from a other device, you can do that over SSH. Use "passwd" to create a temporary password for the root user.

2. **Run the command "archinstall"**

3. **Set following settings**

   - Archinstall language: _English_
   - Keyboard layout: _uk_
   - Mirror region: _Switzerland_
   - Locale language: _en_US_
   - Locale encoding: _UTF-8_
   - Drives: Choose single drive and wipe it
     - Filesystem: ext4
     - Create separate partiton for home: no
   - Encrypton: _none_
   - Bootloader: _GRUB_
   - SWAP: _TRUE_
   - Hostname: Set any hostname
   - Root password: set password
   - Create user:
     - username: <username>
     - Add to sudo group
   - Profile:
     - Desktop i3-wm
     - Use gpu drivers according to the machine you install
   - Audio: pipewire
   - Kernel: linux
   - Additional packages: git openssh
   - Network configuration: Use networkmanager
   - Timezone: Europe/Zurich

   Everything else on default

4. **Start install and when finished enter per chroot**

   - Open terminal and set keyboard layout: "setxkbmap gb"
   - Start sshd service via "sudo systemctl start sshd"

5. **Post arch installation execute the following command with your main user**

```bash
curl -Lks https://raw.githubusercontent.com/rabume/arch-post-install/main/install | /bin/bash
```

This script requires intereactive input, so you have to be present during the installation.

## Manual steps

### Setup Wireguard VPN connection

- Get Wireguard config
- Import config with the nmcli tool

```bash
nmcli connection import type wireguard file wg0.conf
```

### Setup SSH

To setup SSH, you need to copy your SSH keys to the new machine. You can do this with the following command:

```bash
ssh-copy-id username@<ip>
```

### Setup GPG

To setup GPG, you need to copy your GPG keys to the new machine. You can do this with the following command:

```bash
gpg --import <keyfile>
```
