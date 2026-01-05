This is a small section for screen shots on Sway utilizing grimshot, it uses super+shift+a w s to capture (a) selected area (w) active window & (s) screen

For the example given it defaults to the directory: $(xdg-user-dir PICTURES)/screenshots

Screen shot location for my machine, I end up hardcoding the directory like /media/username/tmpfs/screenshot-$(date +"%Y%m%d-%H%M%S").webp

The image format can be swapped with jpg, png or webp (possibly more)

(Optional: I also suggest using zram + add the next line to fstab to create a 1GB RAMDISK for screen shots to reduce disk wear, create directory prior to fstab add) 

tmpfs /media/username/tmpfs tmpfs defaults,size=1G 0 0


Add the following section into your sway config, insert after layout section:


# Take screenshots:
    set $screenshot_out $(xdg-user-dir PICTURES)/screenshots/screenshot-$(date +"%Y%m%d-%H%M%S").webp
    bindsym $mod+Shift+s exec grimshot save screen $screenshot_out
    bindsym $mod+Shift+w exec grimshot save active $screenshot_out
    bindsym $mod+Shift+a exec grimshot save area $screenshot_out
