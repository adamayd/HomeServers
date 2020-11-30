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

### Setting up ssh keys

On the ansible client, create an ansible user without a password (this prevents ssh authentication to the ansible control node). 

```
sudo useradd ansible
```

SSH into the host and creae an ansible user with a password (this allows for the user to invoke `sudo`)

```
sudo useradd ansible
sudo passwd ansible
```
