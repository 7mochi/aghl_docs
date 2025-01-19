---
title: Configuring the Half-Life server
type: docs
prev: docs/setup-linux-server/installing-hlserver
next: docs/setup-linux-server/installing-agmod
weight: 3
---

{{% steps %}}

### Stop the Half-Life server
Before configuring the server, make sure to stop it.

```shell
./hldmserver stop
```

### Configuring startup parameters
You can set up the server's startup parameters by editing the `hldmserver.cfg` file in the LinuxGSM configuration directory.

{{< callout emoji="ℹ️">}}
This guide uses the `nano` text editor, but you can use any text editor you prefer.
{{< /callout >}}

```shell
nano lgsm/config-lgsm/hldmserver/hldmserver.cfg
```

```cfg {filename="lgsm/config-lgsm/hldmserver/hldmserver.cfg"}
## Server IP Port
port="27015"
## Maximum number of players
maxplayers="32"
## Default map to load on startup
defaultmap="crossfire"
## Server configuration file
servercfg="server.cfg"
```

### Customizing the server
To customize your server, edit the `server.cfg` file in the `serverfiles/valve` directory.

```shell
# By default, LinuxGSM names the file hldmserver.cfg
# Rename it to server.cfg as per the startup parameters
mv serverfiles/valve/hldmserver.cfg serverfiles/valve/server.cfg

# Open the server.cfg file for editing
nano serverfiles/valve/server.cfg
```

```txt {filename="serverfiles/valve/server.cfg"}
// Server name
hostname "My Half-Life Server"
// RCON password
rcon_password "myrconpassword"
// Server password (leave empty for no password)
sv_password "test"
```

{{< callout emoji="ℹ️">}}
For a list of server commands and variables, refer to the [Valve Console Command List](https://developer.valvesoftware.com/wiki/Console_Command_List).
{{< /callout >}}

### Start the Half-Life server
Now that the server is configured, you can start it.

```shell
./hldmserver start
```

{{% /steps %}}

With the server successfully configured, you are now ready to install a new mod to transform your Half-Life server. The next step in this guide will walk you through the process of installing Adrenaline Gamer, a mod that offers a distinct gameplay experience tailored for competitive players. Follow the next section for detailed instructions on installing and setting up Adrenaline Gamer.

