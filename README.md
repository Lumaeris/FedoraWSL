# FedoraWSL
**Fedora on WSL 2 (Windows 10 1903 or later, Windows 11) based on [wsldl](https://github.com/yuk7/wsldl)**

![screenshot](https://raw.githubusercontent.com/Lumaeris/FedoraWSL/master/img/screenshot.png)

### [Download](https://github.com/Lumaeris/FedoraWSL/releases)

> [!NOTE]
> Support for WSLg (GUI apps) and WSL1 has not been tested.

## Requirements
* Windows 10 1903 x64 or later, or Windows 11 x64.
* Windows Subsystem for Linux and Virtual Machine Platform features is enabled.

## Install
1. Ensure that WSL is installed via the `wsl --install` command or the app is installed via [GitHub](https://github.com/microsoft/WSL/releases/latest).
2. [Download](https://github.com/Lumaeris/FedoraWSL/releases) the latest installer.
3. Unzip all files to a directory of your choice.
4. Open `Fedora41.exe` to extract the rootfs and register the distribution on WSL.

> [!NOTE]
> The name of the .exe file is the name of the distro to be installed. If you rename this file, you can register the distribution under a different name and thus have multiple installations.

## How-to-Use(for Installed Instance)
#### exe Usage
```dos
Usage :
    <no args>
      - Open a new shell with your default settings.
        Inherit current directory (with exception that %%USERPROFILE%% is changed to $HOME).

    run <command line>
      - Run the given command line in that instance. Inherit current directory.

    runp <command line (includes windows path)>
      - Run the given command line in that instance after converting its path.

    config [setting [value]]
      - `--default-user <user>`: Set the default user of this instance to <user>.
      - `--default-uid <uid>`: Set the default user uid of this instance to <uid>.
      - `--append-path <true|false>`: Switch of Append Windows PATH to $PATH
      - `--mount-drive <true|false>`: Switch of Mount drives
      - `--wsl-version <1|2>`: Set the WSL version of this instance to <1 or 2>
      - `--default-term <default|wt|flute>`: Set default type of terminal window.

    get [setting [value]]
      - `--default-uid`: Get the default user uid in this instance.
      - `--append-path`: Get true/false status of Append Windows PATH to $PATH.
      - `--mount-drive`: Get true/false status of Mount drives.
      - `--wsl-version`: Get the version os the WSL (1/2) of this instance.
      - `--default-term`: Get Default Terminal type of this instance launcher.
      - `--wt-profile-name`: Get Profile Name from Windows Terminal
      - `--lxguid`: Get WSL GUID key for this instance.

    backup [contents]
      - `--tar`: Output backup.tar to the current directory.
      - `--tgz`: Output backup.tar.gz to the current directory.
      - `--vhdx`: Output backup.ext4.vhdx to the current directory. (WSL2 only)
      - `--vhdxgz`: Output backup.ext4.vhdx.gz to the current directory. (WSL2 only)
      - `--reg`: Output settings registry file to the current directory.

    clean
      - Uninstall that instance.

    help
      - Print this usage message.
```

#### Just Run exe
```cmd
>Fedora41.exe
[root@PC-NAME ~]#
```

#### Run with command line
```cmd
>Fedora41.exe run uname -r
5.15.167.4-microsoft-standard-WSL2
```

#### Run with command line with path translation
```cmd
>Fedora41.exe runp echo C:\Windows\System32\cmd.exe
/mnt/c/Windows/System32/cmd.exe
```

#### Change Default User(id command required)

The following is an example of adding a user to the "users" and "wheel" groups and setting it as the default user

_Note: Replace `user` with your chosen user name._

```cmd
>Fedora41.exe run useradd -m -g users -G wheel -s /bin/bash user

>Fedora41.exe config --default-user user

>Fedora41.exe
[user@PC-NAME ~]$
```

#### Set "Windows Terminal" as default terminal
```cmd
>Fedora41.exe config --default-term wt
```

#### How to uninstall instance
```dos
>Fedora41.exe clean
```

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Lumaeris/Lumaeris/refs/heads/main/assets/footer-white.png">
        <img alt="Lumaeris" width="600px" src="https://raw.githubusercontent.com/Lumaeris/Lumaeris/refs/heads/main/assets/footer-dark.png">
    </picture>
</p>
<p align="center">
    <a href="https://github.com/Lumaeris/FedoraWSL/blob/master/LICENSE"><img src="https://img.shields.io/badge/License-MIT-ED592F?style=for-the-badge"/></a>
</p>
