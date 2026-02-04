# Installation 📥

Valt is available for Windows, Linux, and macOS. Choose your operating system's installation method below.

## System Requirements 📋

- **Operating System**: Windows 10/11, Linux (Ubuntu 20.04+, Fedora 35+, etc.) or macOS 11+
- **RAM**: 4 GB (minimum), 8 GB (recommended)
- **Disk Space**: 100 MB for installation + space for your data
- **Internet Connection**: Required for fetching Bitcoin and fiat currency quotes

## Download ⬇️

Visit the [Releases page on GitHub](https://github.com/btcdoomguy/valt/releases) and download the latest version for your operating system.

### 🪟 Windows

1. Download the `Valt-Windows-vXXXX.zip` file (where XXXX is the latest version)
2. Extract to a folder of your choice
3. Run the `Valt.exe` file

### 🐧 Linux

1. Download the `Valt-Linux-vXXXX.zip` file (where XXXX is the latest version)
2. Extract to a folder of your choice
3. Run the `Valt` file

!!! tip "Tip for Linux"
    You can create a shortcut in the applications menu by creating a `.desktop` file in the `~/.local/share/applications/` folder.

### 🍎 macOS

1. Download the `Valt-MacOs-experimental-vXXXX.zip` file (where XXXX is the latest version)
2. Open the DMG file
3. Drag Valt to the Applications folder
4. On first run, you may need to allow execution in **System Preferences > Security & Privacy**

!!! warning "About macOS"
    Valt is compatible with macOS but is not officially supported. Some layout and functionality issues may occur.

## First Run 🎬

When running Valt for the first time, you'll see the initial selection screen with two options:

1. **Create new database** - To start from scratch
2. **Open existing database** - If you already have a Valt data file

### Creating a New Database

1. Click **Create new database**
2. Choose a location to save the `.valt` file
3. Set a **strong password** to protect your data
4. Confirm the password
5. Click **Create**

!!! warning "Important about the password"
    Keep your password in a safe place. If you forget it, **it will not be possible to recover** your data. There is no "forgot my password" option.

### Opening an Existing Database

1. Click **Open existing database**
2. Navigate to the `.valt` file
3. Enter the password
4. Click **Open**

## Updates 🔄

Valt automatically checks for new available versions. When an update is available, you'll see an indicator in the interface.

To update manually:

1. Visit the [Releases page on GitHub](https://github.com/btcdoomguy/valt/releases)
2. Download the latest version
3. Run the new version and delete the old one
4. Your data is preserved in the `.valt` file

## Backup 💾

Your data is in the `.valt` file you created. To backup:

1. Close Valt
2. Copy the `.valt` file to a safe location (external HD, cloud, etc.)
3. Do this regularly!

!!! tip "Backup Tip"
    The `.valt` file is an encrypted SQLite database. You can store it in cloud services like Google Drive or Dropbox, as it's password protected.

## Next Steps ➡️

Now that Valt is installed, go to [Getting Started](primeiros-passos.md) to set up your accounts and start using it.
