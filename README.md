# Unturned Server Setup Guide

## Table of Contents
1. [Introduction](#introduction)
2. [Requirements](#requirements)
3. [Installation](#installation)
   - [Installing SteamCMD](#installing-steamcmd)
   - [Setting Up the Server](#setting-up-the-server)
4. [Configuration](#configuration)
   - [Commands.dat File](#commandsdat-file)
5. [Starting and Stopping the Server](#starting-and-stopping-the-server)
   - [Starting the Server](#starting-the-server)
   - [Stopping the Server](#stopping-the-server)
6. [Connecting to the Server](#connecting-to-the-server)
7. [Using Nano for Configuration](#using-nano-for-configuration)
8. [Troubleshooting](#troubleshooting)
9. [Useful Commands](#useful-commands)
10. [Conclusion](#conclusion)

## Introduction
This repository provides instructions for setting up and running a private Unturned server on Windows 11 using SteamCMD. This setup allows you to play with friends on the PEI map.

## Requirements
- **Windows 11** (or compatible OS)
- **Steam** account
- **SteamCMD** installed
- **Nano** text editor (optional but recommended for editing configuration files)

## Installation

### Installing SteamCMD
1. **Download SteamCMD**:
   - Download SteamCMD from the [official site](https://developer.valvesoftware.com/wiki/SteamCMD#Windows).
   - Extract the contents to a folder (e.g., `C:\SteamCMD`).

2. **Run SteamCMD**:
   - Open PowerShell (run as Administrator).
   - Navigate to the SteamCMD directory:
     ```powershell
     cd C:\SteamCMD
     ```
   - Start SteamCMD:
     ```powershell
     .\steamcmd.exe
     ```

### Setting Up the Server
1. **Set the installation directory**:
   ```bash
   force_install_dir C:\UnturnedServer\
   ```

2. **Login and install the Unturned server**:
   ```bash
   login anonymous
   app_update 1110390 validate
   quit
   ```

## Configuration

### Commands.dat File
Create a `Commands.dat` file in the `C:\UnturnedServer\` directory with the following content:
  ```plaintext
    @SetMap YourDesiredMap
    @SetServerName YourServerName
    @SetMaxPlayers 16
    @SetPort 27015
    @SetPassword (yourpassword) (optional)
  ```

## Starting and Stopping the Server

### Starting the Server
1. **Create a batch file to start the server**:
  - Create a file named `run_start.bat` in `C:\UnturnedServer\` with the following content:
    ```bat
    @echo off
    cd C:\UnturnedServer
    Unturned.exe -nographics -batchmode +secureserver/YourServerName
    ```

2. **To start the server**, double-click the `run_start.bat` file. This will launch the server in a command window.

## Stopping the Server

- To stop the server, simply close the command window running the server. You can also type `exit` in the command window if needed.


## Connecting to the Server
1. Open Unturned on your computer.
2. Click on "Play" and then "Servers".
3. Select "Connect" and enter your server's IP address followed by the port (e.g., `102.168.1.10:27015`).

## Note on IP Address
To find your local IP address, run the following command in PowerShell:
```powershell
Get-NetIPAddress | Where-Object {$_.AddressFamily -eq 'IPv4'} | Select-Object IPAddress
```

Use the shortest IP address listed.

## Using Nano for Configuration

### Installation of Nano
1. Open PowerShell.
2. Run the following command to install Scoop:
   ```powershell
   iwr get.scoop.sh -useb | iex
   ```
   
3. Install Nano:
   ```powershell
   scoop install nano
   ```

### Editing Configuration Files
To edit your `Commands.dat` file or any other text file using Nano:
```bash
nano C:\UnturnedServer\Commands.dat
```
- Save changes with `Ctrl + O` and exit with `Ctrl + X`.

## Troubleshooting
- **Server does not start:** Ensure that the `run_start.bat` file is correctly configured and points to the correct directory.
- **Can’t connect to the server:** Check your firewall settings and ensure the server port (27015) is open.
- **Low RAM Availability:** Make sure that enough RAM is available on your system. Ideally, 16GB is sufficient for a small server.

## Useful Commands

- **Start SERVER**
  ```bash
  run_start.bat
  ```
- **Stop Server:** Close the command window running the server.

- Check Installed Packages with Scoop:
  ```powershell
  scoop list
  ```

- Check Installed Packages with Chocolatey:
  ```powershell
  choco list --local-only
  ```

## Conclusion
  This guide provides a complete setup for running an Unturned server on Windows. With this setup, you can enjoy gaming with friends on the PEI map. For any issues or questions, feel free to reach out.
