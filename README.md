### Various ![](https://raw.githubusercontent.com/swaywm/sway/refs/heads/master/assets/Sway_Logo%2BText_Ver3.png) configurations added to my machine.
🔸Installed: Waybar+rofi+autotiling+slurp+grimshot+foot+nano 🖥️

## Fatigued of manually taking screen shots through cli via grimshot? 🫟
▫️Add bindings to your sway config: use super+shift+a w s to capture [a] selected area [w] active window & [s] entire screen


▫️The main directory for screen shots can be placed within a tmpfs plus zram to reduce wear on your disk which I have left instruction within optional section & should now skip to that [step](https://github.com/Vtekickedinyo/sway.config#zram_tmpfs). 👟
Otherwise:

▫️The default creates the following directory: $(xdg-user-dir PICTURES)/screenshots

### Run the following in terminal to make the directory:
```
mkdir $(xdg-user-dir PICTURES)/screenshots
```
### ◽Insert into ~/.config/sway/config after layout section:
```

# Take screenshots:
    set $screenshot_out $(xdg-user-dir PICTURES)/screenshots/screenshot-$(date +"%Y%m%d-%H%M%S").webp
    bindsym $mod+Shift+s exec grimshot save screen $screenshot_out
    bindsym $mod+Shift+w exec grimshot save active $screenshot_out
    bindsym $mod+Shift+a exec grimshot save area $screenshot_out
```
[Click here](https://github.com/Vtekickedinyo/sway.config#end-of-optional-section) to skip the optional section if you chose the default setting.
### ZRAM_TMPFS 

⭐Optional: I suggest using [zram](https://wiki.debian.org/ZRam) + add [tmpfs](https://www.man7.org/linux/man-pages/man5/tmpfs.5.html) to fstab, creating a 1GB RAMDISK for screen shots to reduce disk wear. Use the following command to create the target directory:
```
sudo mkdir /media/"$USER"/tmpfs -p -m 755
```

◽Edit 'username' within the directory path to your own & add the following to the end of your fstab:

```
tmpfs /media/username/tmpfs tmpfs defaults,size=1G 0 0
```
### ◽Keep in mind that the tmpfs is zeroed out every shutdown/restart.
💭 My own machine runs a ~4GB tmpfs & all downloads target that first as well prior to being moved somewhere more perminant.

 ◽Edit the set $screenshot_out directory path name that's named 'username' to your own & insert into ~/.config/sway/config after layout section:
```

# Take screenshots:
    set $screenshot_out /media/username/tmpfs/screenshot-$(date +"%Y%m%d-%H%M%S").webp
    bindsym $mod+Shift+s exec grimshot save screen $screenshot_out
    bindsym $mod+Shift+w exec grimshot save active $screenshot_out
    bindsym $mod+Shift+a exec grimshot save area $screenshot_out
```
### ⭐End of optional section.

▫️The image format can be swapped with jpg, png or webp (possibly more, jpeg-xl jxl works.)

◽Give Sway a config reload with ctr-shift-c & screenshot keybinds should now function. 🖼️

## Autostarting applications 👣
I unfortunantly have no good way... Only a crude swaymsg command, add to the sway config inside the Layout Stuff portion:
```
    # Start-Up applications per workspace 
    exec swaymsg "workspace number 1; exec foot btop;"
```
> If you populate multiple workspaces with your autostart & want a specific workspace to be visible apon boot add to the end of the list of autostart commands:
```
    exec sway workspace number 1
```
🗨️ It's not a great way of doing things, if an application has long load times it is possible the application opens on the workspace that is currently selected. 
I'll be back to touch more on this, maybe a better way of doing things exist? 💭

## Want to skip manually opening your config file? 
 ▫️This shortcut is opened via super-d drun named sway config directly into nano text editor that gracefully closes the window when you close the editor. This config 'super-d sway' brings up the shortcut. 🐧
 ### ◽Download & mv [swayconf.desktop](https://github.com/Vtekickedinyo/sway.config/raw/refs/heads/main/swayconf.desktop) into 
```
~/.local/share/applications/
```
### ◽Download & mv [sway_logo.jxl](https://github.com/Vtekickedinyo/sway.config/raw/refs/heads/main/sway_logo.jxl) into
 ```
~/.local/share/icons/
```
## Want that Old-Win ctrl+alt+Escape shortcut to open taskman? 
▫️btop in this case. Add in sway config Keybindings 🪟💨
 ###   
 ```
# Start btop
    bindsym ctrl+alt+Escape exec foot btop
```
◽ Sway config reload, the shortcut should be up & running. 👟

❇️ Please consider donating to Sway, and whatever distro of choice of course! ;)
> ▫️If you're thinking of a large donation, consider breaking it down into smaller reoccurring  monthly donations.  💫
# 👋 Thank you 4 stopping by! 
