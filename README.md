### Various ![](https://raw.githubusercontent.com/swaywm/sway/refs/heads/master/assets/Sway_Logo%2BText_Ver3.png) configurations added to my machine.
🔸Waybar+rofi+autotiling+slurp+grimshot+foot+nano 🖥️

## Tired of manually taking screen shots from cli via grimshot? 🫟
▫️Add bindings to your sway config: use super+shift+a w s to capture (a) selected area (w) active window & (s) screen


▫️For the example given it defaults to the directory: $(xdg-user-dir PICTURES)/screenshots
### Run the following to make the directory.
```
mkdir $(xdg-user-dir PICTURES)/screenshots
```
> ⭐Optional: I also suggest using [zram](https://wiki.debian.org/ZRam) + add the next line to fstab to create a [tmpfs](https://www.man7.org/linux/man-pages/man5/tmpfs.5.html) 1GB RAMDISK for screen shots to reduce disk wear, create the target directory prior to fstab add.
### ◽Keep in mind that the tmpfs is zeroed out every shutdown/restart.
▫️My own machine runs a ~4GB tmpfs & all downloads target that first as well before being moved somewhere more perminant.
```
tmpfs /media/username/tmpfs tmpfs defaults,size=1G 0 0
```

 ◽Edit the screenshots directory, should appear as:
 ``` set $screenshot_out /media/username/tmpfs/screenshot-$(date +"%Y%m%d-%H%M%S").webp ```
> ⭐End of optional section.

▫️The image format can be swapped with jpg, png or webp (possibly more, jpeg-xl jxl works.)

◽Add the following section into your sway config, if using optional settings: tweak directory username to your own & insert into ~/.config/sway/config after layout section:
```

# Take screenshots:
    set $screenshot_out $(xdg-user-dir PICTURES)/screenshots/screenshot-$(date +"%Y%m%d-%H%M%S").webp
    bindsym $mod+Shift+s exec grimshot save screen $screenshot_out
    bindsym $mod+Shift+w exec grimshot save active $screenshot_out
    bindsym $mod+Shift+a exec grimshot save area $screenshot_out
```
◽Give Sway a config reload & screenshot keybinds should now function. 🖼️

## Want to skip manually opening your config file? 
 ▫️This shortcut is opened via super-d named sway config that gracefully closes the window when you close the editor. This config 'super-d sway' brings up the shortcut. 🐧
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
❇️ Please consider donating to Sway, and whatever distro of choice of course! ;)
> ▫️If you're thinking of a large donation, consider breaking it down into smaller reoccurring  monthly donations.  💫
# 👋 Thank you 4 stopping by! 
