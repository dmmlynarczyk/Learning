# Void Linux

## Initial Install

- If using the GUI installer, log out of the anon account, and login to root account.
    - Username: `root`
    - Password: `voidlinux`
- In the root account run the following command in terminal:
    - `void-installer`
- The initial bit is pretty straight forward.

## Partitioning

When setting up my partitions I typically have the same hardware configuration of 1TB SSD and 16GB RAM.  
With these hardware specs in mind my partitioning looks like this:  
- Select `cfdisk` option
    - First partition 1G - Type `EFI System` *This is the EFI partition*
    - Second partition 983G - Type `Linux Filesystem` *This is the root partition*
    - Third partition 16G - Type `Linux Swap` *This is the swap partition*
    
- Write changes to disk
- In Filesystems:
    - Choose EFI partition and choose vfat as the filesystem type
        - Mount point is `/boot/efi`
    - Select the root partition and choose btrfs
        - Mount point is `/`
    - Select the swap partition and choose swap

## Post Install

### Updates

- Update the xbps package:
    ```
    sudo xbps-install -u xbps
    ```
- Sync and update packages:
    ```
    sudo xbps-install -Su
    ```

### Install Important Tools

```
sudo xbps-install -S neovim git vscode curl xfce4-whiskermenu-plugin xfce4-screenshooter -y
```
### Install Powershell

1. Download for the newest .tar.gz file on the official GitHub page:
    ```
    curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.3.4/powershell-7.3.4-linux-x64.tar.gz -o /tmp/powershell.tar.gz
    ```

2. Make a new directory and extrat the file to that directory:
    ```
    sudo mkdir -p /opt/microsoft/powershell
    sudo tar -xvzf /tmp/powershell.tar.gz -C /opt/microsoft/powershell
    ```

3. Create a Symlink to make `pwsh` accessible globally:
    ```
    sudo ln -s /opt/microsoft/powershell/pwsh /usr/local/bin/pwsh
    ```

4. Run PowerShell
    ```
    pwsh
    ```

## Flatpak

1. Install Flatpak
    ```
    sudo xbps-install -S flatpak -y
    ```

2. Add the Flathub repository
    ```
    flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
    ```

3. Restart computer

### Install Bitwarden

```
flatpak install flathub com.bitwarden.desktop -y
```

## Quality of Life Changes

- Under **keyboard settings** > **Application Shortcuts** add:
    - `xfce4-popup-whiskermenu` and assign the L Super button to it.
        - This allows you to use the Super button to launce the Whisker menu and quickly type for program names.














