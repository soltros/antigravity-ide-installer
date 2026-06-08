# Antigravity IDE Linux Installer

A shell script to install or update the **Antigravity IDE** system-wide on Linux distributions.

## What it does

When you run `install.sh`, the script performs the following actions:
1. Extracts the provided `.tar.gz` archive to a temporary directory.
2. Locates the root of the application bundle.
3. Installs the application files into `/opt/antigravity-ide`.
4. Sets the required permissions for the `chrome-sandbox` executable.
5. Creates a terminal symlink at `/usr/local/bin/antigravity-ide`.
6. Generates a `.desktop` application shortcut in `/usr/share/applications/`.
7. Cleans up temporary extraction files.

## Prerequisites

- **Antigravity IDE Package:** Download the latest Linux `.tar.gz` package from [https://antigravity.google/download](https://antigravity.google/download).
- **Root Privileges:** The script requires `sudo` or `root` access to write to system directories.
- **Dependencies:** Standard Linux core utilities (`tar`, `cp`, `find`, `ln`, `mkdir`, `chown`, `chmod`).

## Usage

Run the installation script and pass the path to the Antigravity IDE `.tar.gz` package as the first argument:

```bash
# Make the script executable
chmod +x install.sh

# Run the installer
sudo ./install.sh "/path/to/Antigravity IDE.tar.gz"
```

**Updating:** The script can also be used to update the IDE. Running it with a newer `.tar.gz` file will replace the existing installation.

## Uninstallation

To remove the Antigravity IDE from your system, run:

```bash
sudo rm -rf /opt/antigravity-ide /usr/local/bin/antigravity-ide /usr/share/applications/antigravity-ide.desktop
```
