# astro's dotfiles

These are my dotfiles to be used by whoever wishes to, some of the stuff is written by me and other stuff is stolen from other people's dotfiles (mainly typecraft-dev/dotfiles).

I won't be putting a license on this, just please don't make money on this.
This includes putting it in something paid.(idk why you would do either though)

I do prefer hyprland as a tiling window manager and for it to be quite bare bones so this will not turn it into a floating window manager and will only add "*bloat*" that will effect you when you launch them.

# [DISCLAIMER](#important-disclaimer)
# Installation
 


### This will walk you through installing this from either no desktop environment but will still work if you are in one, there are certain instructions for people in a DE.

## Step 1
### Install the packages listed below
**From pacman:**
hyprland hyprpaper hyprlock wofi kitty kate firefox waybar swaync nautilus

or run this command
###
    sudo pacman -Syu hyprland hyprpaper hyprlock wofi ttf-hack-nerd ghostty kate firefox waybar swaync nautilus xdg-desktop-portal-hyprland hyprpicker

<sub/> If you want to you can replace ttf-hack-nerd with nerd-fonts. <br/>
It will require root password right after running.
## Step 2
### Entering hyprland and using the files
<sub/>*If you have a NVidia GPU, go to the [NVidia GPU section](#for-nvidia-gpus)* before proceeding

Here I will walk you through the process of getting the files and using them for the config with just the terminal but I would recommend opening the browser to copy some commands.

### Getting the config files onto the PC
*Most distros come preinstalled with git, hence why it's not on the packages to install at the beginning of the guide. To test if you have git, just run `git`, if you don't have it, run this command:* `sudo pacman -S git`

### If you are already in a desktop environment with a browser don't do the next few steps

Run the `Hyprland` command to enter hyprland.  <br/>
*You will see a warning that says this config was autogenerated, ignore it.*

Press `super+Q` to open kitty(our terminal emulator)  <br/>
Run the `firefox` command to open firefox, go to this page in FireFox (github.com/astrob4t/dotfiles)
### For those of you already on a desktop environment, start following the instructions again.

Scroll down to here and run this command on your terminal:
###
    git clone https://github.com/astrob4t/dotfiles.git

Now press `super+E` to open your file explorer, or just use a file explorer if you're in a different Desktop Environment for this.  <br/>
Enter the dotfiles folder, press `ctrl+h` to show hidden files and folders.(keep this on for your convinience)  <br/>
From here copy the dotfiles folder and navigate to `~/` and paste the .config folder there.

You should see hyprland suddenly reload.  <br/>
Press `super+M` to exit hyprland and run `Hyprland` to reopen it and make sure waybar shows up.

### If you are in a DE already, restart the PC, if you have a greeter, choose hyprland from there or just run `Hyprland` after login instead of whatever you use.

<a name="for-nvidia-gpus"></a>
# For NVidia GPUs

This is where things get quite technical.

Run `Hyprland` to generate and autoconfig, even if it does open, press `super+M` anyways because we want to make sure it always uses the NVidia drivers

### If your distro uses dracut(like endeavouros, what I use), then follow these instructions,you can find out if you have dracut with the command `dracut`, if that says something that's not `bash: dracut: command not found` then you have dracut and follow these instructions.  <br/>
### If you don't have dracut, follow these instructions: https://wiki.hyprland.org/Nvidia/
*I am doing this process completely in terminal because that's how my brain operates, sorry if this makes it hard for you to understand.

Make sure you have the NVidia drivers installed, to install them run `sudo pacman -S nvidia-open`.

Open a terminal and type `cd /etc/dracut.conf.d`  <br/>
Then run the command `touch drivers.conf`, you can name this file whatever you want just make sure it just make sure it ends with '.conf' and doesn't have any spaces.  <br/>
After this run `nano drivers.conf` and type `force_drivers+=" nvidia nvidia_modeset nvidia_uvm nvidia_drm "` exactly.
###  Make sure the file you are using nano on is the same as the file you used touch on
Press `ctrl+x` then `return`.

After this run `cd ~/.config`  <br/>
Run the command `ls` and make sure `hypr` is in the list, if it is then just run `cd hypr` to enter the hypr dir.  <br/>
*(if you type `sl` instead of `ls` a train will go across your screen because of the sl package I had you install earlier)*

### If it's not there
Run `Hyprland` and even if it loads, press `super+M` to close hyprland because we want to make sure it runs the NVidia drivers every time. Now return to the previous step and make sure its there now.

Now run `nano hyprland.conf`.
Now add this to the bottom of that config:
###
    env = LIBVA_DRIVER_NAME,nvidia
    env = __GLX_VENDOR_LIBRARY_NAME,nvidia
    cursor {
    no_hardware_cursors = true
    }

Now return to the normal steps.

<a name="important-disclaimer"></a>
# Disclaimer
### These instructions are made for Arch Linux and were made from memory at 10 PM by a 14 year old with way to much time and knowledge on his hands
