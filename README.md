# Home Server Configurations

## Hardware

* Raspberry Pi 4
* Cana-kit Case, heatsinks, and fan

## Software

* Raspberry Pi OS Lite
* Ansible
* Docker

### Containers

* TP Link Omada Controller Software
* Pi-Hole

## Initial Setup

### Creating Users

On the ansible client, create an ansible user without a password (this prevents ssh authentication to the ansible control node). This may not work on desktop linux if users are required to have a password for the account to be enabled.

```
sudo useradd ansible
```

SSH into the RPi and create an ansible user with a password (this allows for the user to invoke `sudo`)

```
sudo adduser ansible
```

While still on the RPi we need to add a line to the sudoers file.  First set the editor to vim with two commands.

```
sudo apt remove nano
select-editor
```

Then add the following line with `sudo visudo` command.

```
ansible ALL=(ALL) NOPASSWD: ALL
```

### Setting up ssh keys

As your client/control node `ansible` user, run `ssh-keygen` to create the keys.  I've used my local user and have created a different file name from the default `id_rsa`.

Use `ssh-copy-id` to copy the `.pub` file to the Raspberry Pi

```
ssh-copy-id -i <PATH_TO_KEY_FILES>.pub <USER>@<HOSTNAME_OR_IP>
```
