# **Install Hyprland on ArchUTM**
![Arch Linux ARM Logo](https://archlinuxarm.org/public/images/alarm.png)
***
# Setting up Arch
## Arch Installation
1. Download Arch Linux from the UTM Gallery
2. Let it boot and log in as:
	 `alarm login: root`
	 `Password: root`
3. Update the installation with `pacman -Syu`
4. Now install the package `base-devel` like this `pacman -S base-devel` and reboot
## Adding user accounts
1. Change your root password with `passwd`
2. Now create a new user like this
	`useradd -m -G wheel -s /bin/bash yourname`
3. Change your user password with `passwd yourname`
4. Add admin privileges by typing `EDITOR=nano visudo`
	now find this line and delete the Hashtag
	`# %wheel ALL=(ALL:ALL) ALL`
	save with CTRL+O and then CTRL+X
5. You can now safely login to your user account
## Adding the Locale 
1. Run these commands to set all the locals to default english.
	```bash
	sudo locale-gen en_US.UTF-8
	sudo localectl set-locale LANG=en_US.UTF-8
	```

## Changing the hostname
1. Run
	`sudo nano /etc/hostname`

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
1. Run the given command to start sddm at boot
	`sudo systemctl enable --now sddm`
2. You can check on sddm with
	`sudo systemctl status sddm`

## Fixing SDDM
1. Check if this file exists (it probably doesn't)
	`/etc/sddm.conf`
2. If it doesn't go and install `git`
3. go into the home dir by using `cd ~` or simply `cd`
4. then we `sudo git clone https://github.com/LesesTrickshon/install-hyperland-on-archutm.git`
5. now we are going to move it into /etc by using this move command:
	`sudo mv ~/install-hyperland-on-archutm/sddm.conf /etc/sddm.conf`

# Adding a Display to UTM
1. Shut down the arch VM
2. Open the VM Settings via the slider/settings button in the top right.
3. On the left menu bar find the Devices Category. It will most likely be looking like this:
	- Serial
	- Network
	- Sound
4. Press the gray "New" button under them and select "Dispaly"
5. Change the "Emulated Display Card" to `VGA`
6. press the save button and boot up your machine. You will see 2 windows. One for your terminal and one for the display output.
