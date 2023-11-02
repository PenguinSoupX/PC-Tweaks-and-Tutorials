# Re-Install Arch Linux

## Prepare for Reinstallation

- [ ] **chroot** into the existing system.
- [ ] Generate a list of currently installed repository packages:

  **pacman -Qnq > repopackages.txt**

- [ ] Generate a list of currently installed AUR packages:

  **pacman -Qmq > aurpackages.txt**

- [ ] List all Flatpak applications, specifically noting Firefox bookmarks:

    **flatpak list**


## Backup Configuration Files

- [ ] Copy the **fstab** file to preserve your mount configurations for the new system.
- [ ] Copy any configuration files from directories other than your home directory, such as those in the `/etc` directory.

## Reinstallation

- [ ] Wipe the root and EFI partitions to prepare them for the new installation.
- [ ] Install the base system following the Arch Linux installation guide.
- [ ] Reinstall repository packages using the list from **repopackages.txt**:

  **sudo pacman -S $(< repopackages.txt)**


## Install Additional Applications

- [ ] Use **yay** to install AUR packages.
- [ ] Install the **[Chaotic-AUR](https://aur.chaotic.cx/)** Repository for access to binaries from AUR.
- [ ] Use **Flatpak** to install applications, ensuring you reinstall Firefox and import your bookmarks.
- [ ] Optionally, use **Snap** to install any applications not available in the Arch Linux repositories or AUR.

This checklist outlines the steps to reinstall Arch Linux while preserving your configuration files and ensuring you reinstall essential packages and applications.


Make sure to adjust the checklist to your specific needs and preferences.

## Export and Reinstall Flatpak Applications from Old System

If you want to migrate your Flatpak applications from your old system to a new one without manual intervention, follow these steps:

## Export Installed Flatpak Applications

1. Open a terminal on your old system.

2. Run the following command to export a list of installed Flatpak applications, storing the output in a file, for example, `installed_flatpaks.txt`:

    **flatpak list --app --columns=application | xargs echo -n > installed_flatpaks.txt**

   This command will create a file containing a list of application IDs.

## Create a Script to Reinstall Flatpak Applications

3. To automate the reinstallation on the new system, create a script file, e.g., `install_flatpaks.sh`, and edit it with a text editor.

4. Add the following lines to the script to install the Flatpak applications:

   ** #!/bin/bash <br>
    while read -r line; do <br>
        flatpak install flathub "$line" -y <br>
    done < installed_flatpaks.txt <br>
**
   This script reads each line from the `installed_flatpaks.txt` file and uses the `flatpak install` command to reinstall the applications from Flathub.

5. Save the script and make it executable by running the following command in your terminal:

    **chmod +x install_flatpaks.sh**

## Reinstall Flatpak Applications on the New System

6. Transfer the `installed_flatpaks.txt` file and the `install_flatpaks.sh` script to your new system.

7. Open a terminal on your new system and navigate to the directory where you saved the script.

8. Run the script to install the Flatpak applications:

   ** ./install_flatpaks.sh**

   This will automatically reinstall the applications on your new system.

By following these steps, you can efficiently export and reinstall your Flatpak applications on a new system, simplifying the migration process.
