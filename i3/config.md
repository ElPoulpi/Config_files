# Config i3


**A modifier en fonction du Linux**

``Script`` : Chemin à modifier

``Terminal`` : Software à modifier (gnome-terminal, terminator ....)

``Graphic file system`` : Software à modifier (nautilus ....)

``i3bar``: Position à modifier 
```
# i3 config file (v4)
#
# Please see https://i3wm.org/docs/userguide.html for a complete reference!

set $mod Mod1

exec --no-startup-id xrandr -s 1440x900
exec --no-startup-id $wallpapers
exec --no-startup-id nm-applet
exec --no-startup-id blueman-applet
exec --no-startup-id flameshot
exec --no-startup-id pasystray
exec --no-startup-id volumeicon

# Script wallpapers (à rajouter)
#set $wallpapers /home/test/Images/wallpapers
#set $wallpapers_script /home/test/.config_i3/random_wallpaper
#exec --no-startup-id feh --bg-scale /home/test/Images/wallpapers/ubuntu.png
#bindsym $mod+p exec "/bin/bash /home/test/.config_i3/random_lock /home/test/Images/Lock/"
#bindsym $mod+w exec "/bin/bash /home/test/.config_i3/random_wallpaper /home/test/Images/wallpapers/"

# Font
font pango:DejaVu Sans Mono 8


# Use Mouse+$mod to drag floating windows to their wanted position
floating_modifier $mod

# start a terminal
bindsym $mod+BackSpace exec gnome-terminal

# start graphic file system
bindsym $mod+a exec nautilus

# kill focused window
bindsym $mod+F4 kill

# start dmenu (a program launcher)
bindsym $mod+d exec dmenu_run
# There also is the (new) i3-dmenu-desktop which only displays applications
# shipping a .desktop file. It is a wrapper around dmenu, so you need that
# installed.
# bindsym $mod+n exec --no-startup-id i3-dmenu-desktop

# change focus
bindsym $mod+j focus left
bindsym $mod+k focus down
bindsym $mod+l focus up
bindsym $mod+m focus right

# alternatively, you can use the cursor keys:
bindsym $mod+Left focus left
bindsym $mod+Down focus down
bindsym $mod+Up focus up
bindsym $mod+Right focus right

# move focused window
bindsym $mod+Shift+j move left
bindsym $mod+Shift+k move down
bindsym $mod+Shift+l move up
bindsym $mod+Shift+m move right

# alternatively, you can use the cursor keys:
bindsym $mod+Shift+Left move left
bindsym $mod+Shift+Down move down
bindsym $mod+Shift+Up move up
bindsym $mod+Shift+Right move right

# split in horizontal orientation
bindsym $mod+h split h

# split in vertical orientation
bindsym $mod+v split v

# enter fullscreen mode for the focused container
bindsym $mod+f fullscreen toggle

# change container layout (stacked, tabbed, toggle split)
bindsym $mod+s layout stacking
bindsym $mod+z layout tabbed
bindsym $mod+e layout toggle split

# toggle tiling / floating
bindsym $mod+Shift+space floating toggle

# change focus between tiling / floating windows
bindsym $mod+space focus mode_toggle

# focus the parent container
bindsym $mod+q focus parent



# focus the child container
#bindsym $mod+d focus child

# Define names for default workspaces for which we configure key bindings later on.
# We use variables to avoid repeating the names in multiple places.
set $ws0 "WELCOME STRANGER"
set $ws1 "1"
set $ws2 "2"
set $ws3 "3"
set $ws4 "4"
set $ws5 "5"
set $ws6 "6"
set $ws7 "7"
set $ws8 "8"
set $ws9 "9"
set $ws10 "10"

# switch to workspace
#bindsym $mod+twosuperior workspace $ws0
bindsym $mod+ampersand workspace $ws1
bindsym $mod+eacute workspace $ws2
bindsym $mod+quotedbl workspace $ws3
bindsym $mod+apostrophe workspace $ws4
bindsym $mod+parenleft workspace $ws5
bindsym $mod+minus workspace $ws6
bindsym $mod+egrave workspace $ws7
bindsym $mod+underscore workspace $ws8
bindsym $mod+ccedilla workspace $ws9
bindsym $mod+agrave workspace $ws0

# move focused container to workspace
bindsym $mod+Shift+twosuperior move container to workspace $ws0
bindsym $mod+Shift+ampersand move container to workspace $ws1
bindsym $mod+Shift+eacute move container to workspace $ws2
bindsym $mod+Shift+quotedbl move container to workspace $ws3
bindsym $mod+Shift+apostrophe move container to workspace $ws4
bindsym $mod+Shift+5 move container to workspace $ws5
bindsym $mod+Shift+minus move container to workspace $ws6
bindsym $mod+Shift+egrave move container to workspace $ws7
bindsym $mod+Shift+underscore move container to workspace $ws8
bindsym $mod+Shift+ccedilla move container to workspace $ws9
bindsym $mod+Shift+agrave move container to workspace $ws10

# reload the configuration file
bindsym $mod+Shift+c reload
# restart i3 inplace (preserves your layout/session, can be used to upgrade i3)
bindsym $mod+Shift+r restart
# exit i3 (logs you out of your X session)
bindsym $mod+Shift+e exec "i3-nagbar -t warning -m 'You pressed the exit shortcut. Do you really want to exit i3? This will end your X session.' -B 'Yes, exit i3' 'i3-msg exit'"

# Sound / light / screenshooter
bindsym XF86AudioMute        exec --no-startup-id amixer set Master toggle
bindsym XF86AudioRaiseVolume    exec --no-startup-id amixer set Master 10%+
bindsym XF86AudioLowerVolume    exec --no-startup-id amixer set Master 10%-
bindsym XF86MonBrightnessDown	exec --no-startup-id "sudo /bin/backlight moins"
bindsym XF86MonBrightnessUp exec --no-startup-id "sudo /bin/backlight plus"
bindsym Print exec xfce4-screenshooter


# resize window (you can also use the mouse for that)
mode "resize" {
        # These bindings trigger as soon as you enter the resize mode

        # Pressing left will shrink the window’s width.
        # Pressing right will grow the window’s width.
        # Pressing up will shrink the window’s height.
        # Pressing down will grow the window’s height.
        bindsym j resize shrink width 10 px or 10 ppt
        bindsym k resize grow height 10 px or 10 ppt
        bindsym l resize shrink height 10 px or 10 ppt
        bindsym m resize grow width 10 px or 10 ppt
        # same bindings, but for the arrow keys
        bindsym Left resize shrink width 10 px or 10 ppt
        bindsym Down resize grow height 10 px or 10 ppt
        bindsym Up resize shrink height 10 px or 10 ppt
        bindsym Right resize grow width 10 px or 10 ppt

        # back to normal: Enter or Escape or $mod+r
        bindsym Return mode "default"
        bindsym Escape mode "default"
        bindsym $mod+r mode "default"
}

bindsym $mod+r mode "resize"

# Start i3bar to display a workspace bar (plus the system information i3status
# finds out, if available)
bar {
        status_command i3status
        position top
}

```

### Script wallpapers
```
soon
```

### Script lock wallpapers
```
soon
```
