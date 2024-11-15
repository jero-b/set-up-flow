# LINUX DEBIAN WF POST INSTALL
What to do after installing Linux Debian Distribution.
Remember to ignore any brackets[] you see, bracket are for emphasis only.
Remember to set the correct date and time according to your timezone.

## 1. ADD USER TO SUDOER GROUP
In terminal: log in as root.

	su -
	or:
	su
Then:

	sudo visudo
	or:
	sudo nano /etc/sudoers
	
Edit the file, find the following:

	[%sudo   ALL=(ALL:ALL) ALL]
	
Below that add:

	[username]   ALL=(ALL:ALL) ALL
Remember to change the [username] to your account username that you want to add in sudoer group. (ctrl+o) to save, press (enter) and then (ctrl+x) to exit the editor.

-To check: in terminal:
	
	sudo -l
	
If the sudoers file is missing or removed, reinstall the package with this command:

	sudo apt install sudo

## 2. ENABLE SOFTWARE AND UPDATE.

- [ ] Find the [SOFTWARE and UPDATE] app.
- [ ] Enable all check-boxes in the [Debian Software] panel.
- [ ] Choose your preferred server or you can leave it by default. Preferably the Main Server.
- [ ] Go to the [OTHER SOFTWARE] tab and uncheck the CD-Rom source.
- [ ] Close the app, click Reload.
	
## 3. UPDATE SECURITY UPDATES. (Optional)
In terminal:
	
	sudo apt install update
	sudo apt install unattended-upgrades

To check:
	
	sudo dpkg-reconfigure unattended-upgrades

## 4. INSTALL GRAPHIC DRIVERS. (If you don't have NVIDIA GPU or AMD GPU skip this.) 
In terminal for NVIDIA:
	
	sudo apt install nvidia-driver firmware-misc-nonfree

In terminal for AMD: log in as root/su

 	apt-get install firmware-amd-graphics libgl1-mesa-dri libglx-mesa0 mesa-vulkan-drivers xserver-xorg-video-all
	
## 5. FIREWALL. (Recommended if you connect always in public networks)
In terminal:
	
	sudo apt install gufw

To check:
Search "firewall" in the app list. You can see a firewall app.

## 6. INSTALL FLATPAK
In terminal:
	
	sudo apt install flatpak

Flatpak Extension for GNOME SOFTWARE:
	
	sudo apt install gnome-software-plugin-flatpak

Flatpak Extension for KDE DISCOVER:

	sudo apt install plasma-discover-backend-flatpak

Enable Flathub Repo:

	sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

To check:
	
	flatpak --version
	
## 7. BOOT DESIGN. (Not Recommended Very Optional, For Aesthetic)
In terminal:
	
	sudo apt install plymouth plymouth-themes

Display start up animation:
	
	sudo nano /etc/default/grub

Find the:
	
	GRUB_CMDLINE_LINUX_DEFAULT='quiet'

change to:
	
	GRUB_CMDLINE_LINUX_DEFAULT='quiet splash'
save it by pressing "ctrl+o", "Enter", then "ctrl+x"

To check:
	
	sudo update-grub

Reboot your system to see.

## 8. UNINSTALL BLOATWARE GAMES IN GNOME
In terminal:

	sudo apt remove gnome-games
	sudo apt autoremove
	
## 9. CHECK HARDWARES
Check If everything works fine
In terminal:
	
	sudo apt install lshw
	lshw

or:
	
	sudo lshw

or:
	
	sudo lshw -short
	other options:
	lspci
	lsusb
	lscpu
	sudo dmidecode -t memory
	sudo dmidecode -t system
	sudo dmidecode -t bios
	sudo dmidecode -t processor

Manual checking, one by one operate your devices:
	
	keyboard
	mouse/touchpad
	wifi
	usb ports
	speaker
	monitor
	battery
	hardisk
	bluetooth
	and any other.

