---
title: Installing Adrenaline Gamer Mod
type: docs
prev: docs/setup-linux-server/configuring-hlserver
weight: 4
---

{{% steps %}}

### Create a Temporary Directory for AGMod Installation
Create a temporary directory to hold the installation files.

```shell
mkdir tmp && cd tmp
```

### Download the latest AGMod release
Download the latest release of Adrenaline Gamer Mod from the official source.

```shell
wget http://openag.pro/latest/ag.7z
```

### Install AGMod on the Server
Extract and move the AGMod files to the correct directory.

```shell
# Extract the AGMod files
7z x ag.7z
# Remove cheats.dat file
rm ag/cheats.dat
# Move the AGMod files to the serverfiles directory
mv ag ../serverfiles/
# Copy server.cfg to the serverfiles/ag directory
cp ../serverfiles/valve/server.cfg ../serverfiles/ag/
```

### Cleanup the temporary directory
Remove the temporary directory after installation.

```shell
cd .. && rm -rf tmp
```

### Configuring startup parameters
Modify the launch parameters to specify AGMod as the game mod.
```shell
nano lgsm/config-lgsm/hldmserver/hldmserver.cfg
```

```cfg {filename="lgsm/config-lgsm/hldmserver/hldmserver.cfg"}
# Start parameters for AGMod
startparameters="-game ag -strictportbind +ip ${ip} -port ${port} +clientport ${clientport} +map ${defaultmap} +servercfgfile ${servercfg} -maxplayers ${maxplayers}"
```

### Start the AGMod server
Start the server with the updated configuration.

```shell
./hldmserver start
```

{{% /steps %}}