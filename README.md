# Andino Ansible Configuration

This repository contains Ansible configurations for managing and automating the setup and configuration of an [Andino](https://github.com/Ekumen-OS/andino/) robot. It uses `ansible-pull` to pull the configurations directly from this repository and apply them to an Andino robot.

## Table of Contents

- [Requirements](#requirements)
- [Setup Instructions](#setup-instructions)
  - [Install Ansible](#install-ansible)
  - [Running ansible-pull](#running-ansible-pull)
- [Configuration Files](#configuration-files)
- [License](#license)

## Requirements

- An [Andino](https://github.com/Ekumen-OS/andino/) robot running Ubuntu (22.04 or 24.04)
- Ansible 2.9+ installed on the robot
- Access to this GitHub repository or the Git URL

## Setup Instructions

### 1. Flash the SDCard for your Andino

Use the official [Raspberry Pi Imager](https://www.raspberrypi.com/software/) to flash an Ubuntu robot (22.04 or 24.04) image to an SDCard. Make sure to configure the WiFi, hostname and if possible add you ssh public key in the settings for the robot.

### 2. Connect to your robot via ssh
#### From an Ubuntu machine

```bash
ssh andino.local # or change andino.local for the ip address of your robot
````
#### From a Windows machine

Use PuTTY or a similar ssh client to connect to `andino.local` or the ip address of your robot.

### 2. Install Ansible

Before you can use `ansible-pull`, you must have Ansible installed on your robot. Follow the installation steps for your operating system:

#### Ubuntu/Debian

```bash
sudo apt update
sudo apt install -y ansible
```

### 3. Running ansible-pull
ansible-pull allows you to pull the latest playbooks and roles from a Git repository and apply them directly to the robot. To run ansible-pull, follow these steps:

  1. Run ansible-pull to apply the Ansible configuration from the repository to the robot:

  ```bash
  ansible-pull -U https://github.com/garyservin/andino_ansible_configuration.git -K
  ```

  Explanation of the command:

  - -U: Specifies the URL of the Git repository where the Ansible playbook is stored.
  - -K: Ansible will ask you for your user's password once at the beginning of the deploy
  
  The ansible-pull command will download the latest version of the repository and apply the configurations to your robot.

## Configuration Files
This repository includes the following main files:

- playbook.yml: The main Ansible playbook that defines the configuration tasks to be executed on the robot.
- roles/: A directory containing reusable Ansible roles.
- inventory/: Defines the inventory of hosts to be configured

Feel free to modify or extend the playbook and roles as per your infrastructure and requirements.

## License
This repository is licensed under the Apache-2.0 license.
