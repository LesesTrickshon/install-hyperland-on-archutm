# Setting up Arch
## Arch Installation
1. Download Arch Linux from the UTM Gallery
2. Let it boot and log in as:
	 `alarm login: root`
	 `Password: root`
3. update the installation with `pacman -Syu` and reboot
4. now install the package `base-devel` like this `pacman -S base-devel`and reboot again
## Adding user accounts
1. Change your root password with `passwd`
2. now create a new user like this
	`useradd -m -G wheel -s /bin/bash yourname`
3. change your user password with `passwd yourname`
4. add admin privileges by typing `EDITOR=nano visudo`
	now find this line and delete the Hashtag
	`# %wheel ALL=(ALL:ALL) ALL`
	save with CTRL+O and then CTRL+X
5. you can now safely login to your user account
## Adding the Locale 
1. run
	 `nano /etc/locale.gen
2. uncomment the line:
	`#en_US.UTF-8 UTF-8`
## Changing the hostname
1. run
	`nano /etc/hostname`

# Setting up Wayland
## Downloading all packages
All the packages we need are:
- `wayland`
- `sddm`
- `hyprland`
- `kitty`
- `firefox`
	*install them with the `--needed` flag*
## Enabling SDDM
1. run the given command to start sddm at boot
	`sudo systemctl enable sddm`
2. now also add this. This should open sddm after but it doesnt because we haven't set out display yet.
	`sudo systemctl start sddm`
3. you can check on sddm with
	`sudo systemctl status sddm`
