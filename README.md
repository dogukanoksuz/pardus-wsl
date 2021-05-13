# PardusWSL

https://dogukan.dev/pardus-wsl-kurulumu.html

Pardus on WSL (Windows 10 FCU or later)
based on [DistroLauncher](https://github.com/microsoft/WSL-DistroLauncher/)

## 💻Requirements
* Windows 10 1709 Fall Creators Update 64bit or later.
* Windows Subsystem for Linux feature is enabled.
* Update for Windows Subsystem for Linux 2 is required.

## 💾Install
### 📁files
#### 1. [Download](https://github.com/dogukanoksuz/PardusWSL/releases/latest) installer files

#### 2. Put Pardus.exe and install.tar.gz in same folder.
Please select a folder that has full access permission.
For example 'Program Files' can not be used.

#### 3. Run Pardus.exe to Extract rootfs and Register to WSL
Exe filename is using to the instance name to register.
If you rename it you can register with a different name and have multiple installs.

#### 4. Upgrade it to WSL2
You can upgrade it with wsl --set-version Pardus 2 command.

## 📝How-to-Use(for Installed Instance)
#### exe Usage
```dos
Usage :
    <no args>
      - Open a new shell with your default settings.

    run <command line>
      - Run the given command line in that distro. Inherit current directory.

    runp <command line (includes windows path)>
      - Run the path translated command line in that distro.

    config [setting [value]]
      - `--default-user <user>`: Set the default user for this distro to <user>
      - `--default-uid <uid>`: Set the default user uid for this distro to <uid>
      - `--append-path <on|off>`: Switch of Append Windows PATH to $PATH
      - `--mount-drive <on|off>`: Switch of Mount drives
      - `--default-term <default|wt|flute>`: Set default terminal window

    get [setting]
      - `--default-uid`: Get the default user uid in this distro
      - `--append-path`: Get on/off status of Append Windows PATH to $PATH
      - `--mount-drive`: Get on/off status of Mount drives
      - `--wsl-version`: Get WSL Version 1/2 for this distro
      - `--default-term`: Get Default Terminal for this distro launcher
      - `--lxguid`: Get WSL GUID key for this distro

    backup [contents]
      - `--tar`: Output backup.tar to the current directory
      - `--reg`: Output settings registry file to the current directory

    clean
      - Uninstall the distro.

    help
      - Print this usage message.
```

## Errors
### Fixing locale error

Open /etc/default/locale with sudo
Change contents with this lines:
```
LC_CTYPE="en_US.UTF-8"
LC_ALL="en_US.UTF-8"
LANG="en_US.UTF-8"
```

and use this command:
```
sudo dpkg-reconfigure locales
```

then restart WSL with:
```
wsl.exe --shutdown
```

## Activating systemd daemon
DamionGans created a WSL2 systemd daemon activator. Use on clean installs, i didn't tried on used systems.
https://github.com/DamionGans/ubuntu-wsl2-systemd-script

Just clone the folder and run the script as sudo with --force argument.
