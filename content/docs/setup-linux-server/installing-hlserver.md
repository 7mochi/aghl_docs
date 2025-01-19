---
title: Installing the Half-Life server
type: docs
prev: docs/setup-linux-server/prerequisites
next: docs/setup-linux-server/configuring-hlserver
weight: 2
---

{{% steps %}}

### Download LinuxGSM
```shell
curl -Lo linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh hldmserver
```
### Setup Steam Credentials
Before installing the Half-Life server, we will log in to our Steam account. It's recommended to create a new Steam account instead of using your primary account for security reasons.

We will run the LinuxGSM command to initiate the Half-Life server installation, but when prompted to proceed, select "no." This step is only to generate the necessary configuration files where we will enter the Steam account credentials.

```shell
./hldmserver install

# Choose no when asked to proceed
```

Next, enter your Steam credentials in the `secrets-hldmserver.cfg` file located in the LinuxGSM directory.
```shell
nano lgsm/config-lgsm/hldmserver/secrets-hldmserver.cfg
```

```cfg {filename="lgsm/config-lgsm/hldmserver/secrets-hldmserver.cfg"}
## SteamCMD Login
steamuser="my_steam_username"
steampass="my_steam_password"
```

{{< callout emoji="ℹ️">}}
The secret config file is designed to store sensitive information such as Steam login credentials separately from the main configuration files. This allows server admins to back up their configurations while keeping sensitive data excluded. It's particularly useful for admins creating version-controlled skeleton configurations with Git that may be made public.

However, please note that the secret config file is NOT encrypted or more secure than other configuration files.
{{< /callout >}}

### (Optional) Install the Pre-anniversary version
If you prefer not to use the latest updates from Half-Life's Anniversary Update (HL25), you can switch to the `steam_legacy` branch. To do this, specify it in the `common.cfg` file located in the LinuxGSM directory.

```shell
nano lgsm/config-lgsm/hldmserver/common.cfg
```

```cfg {filename="lgsm/config-lgsm/hldmserver/common.cfg"}
branch="steam_legacy"
```

### Install the Half-Life server using LinuxGSM
Now that everything is ready, you can install the Half-Life server using the following command.

```shell
./hldmserver install
```

Follow the on-screen instructions provided by LinuxGSM during the installation process.

{{< callout emoji="ℹ️">}}
During the game server installation, if the user has sudo permissions, LinuxGSM will attempt to install any missing dependencies automatically.

If LinuxGSM fails to install the required dependencies, you will need to install them manually using your distribution's package manager. Refer to your distribution's documentation for the correct commands and package names.
{{< /callout >}}

### Start the Half-Life server
Now that the server is installed, you can start it with the following command.

```shell
./hldmserver start
```

{{< callout emoji="ℹ️">}}
For additional LinuxGSM commands, refer to the [LinuxGSM documentation](https://docs.linuxgsm.com/commands).
{{< /callout >}}

{{% /steps %}}

With the server successfully installed, you are now ready to proceed with configuring your Half-Life server. This includes increasing the number of player slots, setting a default map to load on startup, and other customizations. Follow the next section for detailed instructions on server configuration.