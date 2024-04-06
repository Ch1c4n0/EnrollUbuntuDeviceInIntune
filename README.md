# Enroll Ubuntu Device In Intune

## Prerequisites

- Ubuntu Desktop 22.04 or 20.04 LTS (With GNOME desktop enviroment)
- MS recommendation: Enable disk encription during the setup (It is easier to enable this directly during the setup)
- Microsoft Edge version >=102.X (To validate CA by accessing company ressources)
- Microsoft Intune app (Needed to enroll the device)

## Install Ubuntu

-Download Ubuntu from the official source
-The recommend system requirements: 2 GHz dual-core processor / 4 GB system memory / 25 GB of free hard drive space
-Create an boot stick or insert the iso in a vm (in my case I use a VM)
-Install Ubuntu

## Install Edge on ubuntu
### Open a Terminal and execute the following commands to install the edge browser:
    sudo apt install software-properties-common apt-transport-https wget
    wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/edge stable main"
    sudo apt install microsoft-edge-dev
    sudo apt update
    sudo apt upgrade


## Install Intune app

1. Install Curl:

       sudo apt install curl gpg


2. Install the Microsoft package signing key.

#### For Ubuntu 20.04:

    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
    sudo install -o root -g root -m 644 microsoft.gpg /usr/share/keyrings/
    sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft.gpg] https://packages.microsoft.com/ubuntu/20.04/prod focal main" > /etc/apt/sources.list.d/microsoft-ubuntu-focal-prod.list'
    sudo rm microsoft.gpg


#### For Ubuntu 22.04:

    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
    sudo install -o root -g root -m 644 microsoft.gpg /usr/share/keyrings/ 
    sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft.gpg] https://packages.microsoft.com/ubuntu/22.04/prod jammy main" > /etc/apt/sources.list.d/microsoft-ubuntu-jammy-prod.list' 
    sudo rm microsoft.gpg


Install the Microsoft Intune app:

    sudo apt update
    sudo apt install intune-portal
    Reboot your device.




Version 1.0 2024/04/06
