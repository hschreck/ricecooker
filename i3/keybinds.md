# Keybinds in i3
All configuration for i3 is in the config file, commonly located in ```~/.config/i3/config```.

## Set Mod Key
To set the modifier key, add the following line to your ```config```:

`set $mod Mod1`

The above example will set your Alt key as the modifier.  Many users also like using the Super key ("Windows" key):

`set $mod Mod4`

## Extra modifier keys
There are other keys that are supported for adding to keybinds, other than the standard letter keys.

| Key    | i3 name |
| ---    | --------|
| Shift  | Shift   |
| Return | Return  |
| Ctrl   | Control |
| Alt    | Mod1    |
| Super  | Mod4    |


## Set floating modifier

Since i3 is a tiling window manager, most windows will not be floating.  On the occasions you have one that you need to move, using the floating modifier to move it.  To set the modifier, use the `floating_modifier` keyword, as follows:

`floating_modifier $mod`

Note that this is the default keybind, and allows you to move a floating window by pressing the mod key and dragging with your mouse.

## Basic Command Keybinds
Keybinds in i3 are generally done using the `bindsym` keyword.

Examples:

| Action                                      | Keybind |
| ------                                      | ------- |
| Make Focused Window Fullscreen              | `bindsym $mod+f fullscreen toggle`|
| Set a vertical split (top + bottom windows) | `bindsym $mod+v split v` |
| Set a horizontal split (side by side)       | `bindsym $mod+h split h` |
| Change to workspace 1                       | `bindsym $mod+1 workspace 1`|
| Move focused window to workspace 1          | `bindsym $mod+Shift+1 move container to workspace 1` |


### Binding applications
i3 supports binding keys to any command available to a system, using the same syntax used for other keybinds, along with the `exec` keyword.

A few examples of application keybinds:

| Application | Keybind Line |
| ------------| -------------|
| Google Chrome | `bindsym $mod+g exec google-chrome`|
| dmenu         | `bindsym $mod+d exec --no-startup-id dmenu`        |

### Binding rofi
Rofi is a dmenu-inspired application launcher and window switcher.

To use rofi with a keybind, you'll need to run the command a specific way:

`bindsym $mod+d exec rofi -show run`

### Binding terminals
i3 comes, by default, with the `i3-sensible-terminal` script.  This will run through a list of terminal emulators that i3 deems sensible for its use and launch the first one it finds.  To get a terminal using `i3-sensible-terminal`:

`bindsym $mod+Return exec i3-sensible-terminal`

If you want to run a specific terminal, simply substitute its name in the above command, e.g. `bindsym $mod+Return exec termite`.

## Setting Resize
Unlike WMs most people are used to, i3 does not support dragging windows to resize them.  Resizing is done using the keyboard.

By default, i3 supports a "resize" mode.

````
mode "resize" {
        # These bindings trigger as soon as you enter the resize mode

        # Pressing left will shrink the window’s width.
        # Pressing right will grow the window’s width.
        # Pressing up will shrink the window’s height.
        # Pressing down will grow the window’s height.
        bindsym j resize shrink width 10 px or 10 ppt
        bindsym k resize grow height 10 px or 10 ppt
        bindsym l resize shrink height 10 px or 10 ppt
        bindsym semicolon resize grow width 10 px or 10 ppt

        # same bindings, but for the arrow keys
        bindsym Left resize shrink width 10 px or 10 ppt
        bindsym Down resize grow height 10 px or 10 ppt
        bindsym Up resize shrink height 10 px or 10 ppt
        bindsym Right resize grow width 10 px or 10 ppt

        # back to normal: Enter or Escape
        bindsym Return mode "default"
        bindsym Escape mode "default"
}
````

However, note above that the keybinds are only active in `Resize` mode.  To set a keybind to enter `Resize` mode:

`bindsym $mod+r mode "resize"`

In this example, windows grow and shrink using vim-like keybinds, as well as the arrow keys.  These keybinds work on the currently focused window, but focus can change using the mouse or keyboard.

## Setting media keys
Out of the box, i3 does not support media keys on keyboards, but does support the keybinds for it.

To set media keys, using the following keys to run the appropriate command (often using PulseAudio or `playerctl`):

| Key | Key Name |
|-----| -------- |
| Volume Up | `XF86AudioRaiseVolume` |
| Volume Down | `XF86AudioLowerVolume` |
| Volume Mute | `XF86AudioMute` |
| Play | `XF86AudioPlay` |
| Next | `XF86AudioNext` |
| Prev | `XF86AudioPrev` |
