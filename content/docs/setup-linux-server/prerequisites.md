---
title: Prerequisites
type: docs
prev: docs/setup-linux-server/
next: docs/setup-linux-server/installing-hlserver
weight: 1
---

{{% steps %}}

### Login via SSH
Log in to your server as the root user.

```shell
ssh root@your_server_ip
```
### Update your system
Update your system to ensure stability and compatibility when setting up the Half-Life server.

```shell
# Debian-based distributions (Ubuntu, Debian, etc.)
apt update -y && apt upgrade -y
# Red Hat-based distributions (Fedora, CentOS, etc.)
dnf update -y
# Arch-based distributions (Arch, Manjaro, etc.)
pacman -Syu
# OpenSUSE
zypper update
```

If your distribution isn't listed above, refer to the official documentation for your operating system.

### Creating a user
Create a new user to manage the game server, then add them to the `sudo` group.

```shell
adduser hlserver
usermod -aG sudo hlserver
```
{{< callout emoji="ℹ️">}}
For security best practices, make sure you set a strong password for the new user.
{{< /callout >}}

### Changing to the new user
Switch to the newly created user to continue the setup.

```shell
su - hlserver
```

{{% /steps %}}

With the prerequisites complete, you're ready to install the Half-Life server using LinuxGSM. Follow the next section for detailed instructions on installation and configuration.