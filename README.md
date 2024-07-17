## Linux Unit File for Minecraft Server

This is a unit file to stop and start Minecraft server using systemd.

This file must be placed in `/etc/systemd/system`

Please modify the **Description** and **WorkingDirectory** to use this unit file.

> **For those who are not familiar with unit file, here are some of the additional information**
>
> Description=xxxxx is a description that shown when running `sudo systemctl status minecraft.service`
>
> WorkingDirectory=xxxx is the folder that the server is located, recommanded to put it inside /opt/ or /srv/ (eg /opt/minecraft_server)
>
> Whenever you modified the file, please run `sudo systemctl daemon-reload` to update the systemd

---

To use this script, user named `minecraft` must present in the server. To create it please run `sudo useradd -s /bin/bash -m minecraft`, then `sudo passwd minecraft` to assign a password to the user.

Screen command must also need to be installed. To install it on Ubuntu, please run `sudo apt install screen`

A `start.sh` bash script is recommended, you can generate it in here: [Start Script Generator | PaperMC Docs](https://docs.papermc.io/misc/tools/start-script-gen)

In this unit file, it will automatically execute the `./start.sh` file located in the in the root directory of the Minecraft server using a screen instance as the user `minecraft`.

---

**To enable the auto-start of the server during the boot process, please run**
`sudo systemctl enable minecraft.service`

**To disable the auto-start of the server during the boot process, please run**
`sudo systemctl disable minecraft.service`

**To start the server manually, please run**
`sudo systemctl start minecraft.service`

**To stop the server manually, please run**
`sudo systemctl stop minecraft.service`

---

For more information regarding systemd and unit file, please refer to this article [systemd - ArchWiki (archlinux.org)](https://wiki.archlinux.org/title/systemd)
