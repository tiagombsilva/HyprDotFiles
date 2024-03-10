# HyprV2
An improved Hyprland deployment

collection of dot config files for hyprland with a simple install script for a fresh Arch linux with yay

# Step 1 Arch
Use archinstall script to install a minimal setup without DE.
I opted for btfrs, systemd, pipewire, no DE and git, base-devel packages.

# Step 2 Hypr instalation
First install yay package manager and then
run the attached script "set-hypr" to install everything for you.

# Dual boot Windows 11
```
    sudo fdisk -l # check disks
    sudo mount /dev/nvme0n1p1 /run/mount # mount EFI Windows partition
    mkdir /boot/EFI/Windows # create Windows boot folder on systemd
    cp /run/mount/EFI/Microsoft/Boot /boot/EFI/Windows # copy Windows bootloader to systemd 
    touch /boot/loader/entries/windows.conf
    # Write below the two lines below
    title Windows 11
    efi /EFI/Windows/bootmgfw.efi
```

Below is a list of the packages that will be installed

- hyprland-bin: This is the Hyprland compositor
- kitty: This is the default terminal
- waybar-hyprland: This is a fork of waybar with Hyprland workspace support
- swww: This is used to set a desktop background image
- swaylock-effects: This allows for the locking of the desktop its a fork that adds some editional visual effects
- wofi: This is an application launcher menu
- wlogout: This is a logout menu that allows for shutdown, reboot and sleep
- mako: This is a graphical notification daemon
- xdg-desktop-portal-hyprland-git: xdg-desktop-portal backend for hyprland
- swappy: This is a screenshot editor tool
- grim: This is a screenshot tool it grabs images from a Wayland compositor
- slurp: This helps with screenshots, it selects a region in a Wayland compositor
- thunar: This is a graphical file manager
- polkit-gnome: needed to get superuser access on some graphical application
- python-requests: needed for the weather module script to execute
- pamixer: This helps with audio settings such as volume
- pavucontrol: GUI for managing audio and audio devices
- brightnessctl: used to control monitor and keyboard bright level
- network-manager-applet: Applet for managing network connection
- gvfs: adds missing functionality to thunar such as automount usb drives
- thunar-archive-plugin: Provides a front ent for thunar to work with compressed files
- file-roller: Backend set of tools for working with compressed files
- btop: Resource monitor that shows usage and stats for processor, memory, disks, network and processes.
- pacman-contrib: adds additional tools for pacman. needed for showing system updates in the waybar
- starship: allows to customize the shell prompt
- ttf-jetbrains-mono-nerd: Som nerd fonts for icons and overall look
- noto-fonts-emoji: fonts needed by the weather script in the top bar
- lxappearance-gtk3: used to set GTK theme
- xfce4-settings: set of tools for xfce, needed to set GTK theme
- sddm-git: developement version of SDDM which is a display manager for graphical login
- sddm-sugar-candy-git: an sddm theme my theme is based on (copy of)
# optional packages
- bluez: the bluetooth service
- bluez-utils: command line utilities to interact with bluetooth devices
- blueman: Graphical bluetooth manager

# Other problems
- container with no access to host vpn using systemd https://wiki.archlinux.org/title/Systemd-resolved#DNS
- gpg signing with intellij use pinentry-program pinentry-gnome3 on ~/.gnupg/gpg-agent.conf if error use too: export GPG_TTY=$(tty)

