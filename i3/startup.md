# Startup in i3
i3 supports a simple way to execute commands on startup, using the `exec` keyword, in your i3 config file:

`exec command`

## Compton
The `compton` compositor is useful if you're looking to have transparency in your setup.  To start it up on login:

`exec --no-startup-id compton -b`

The `--no-startup-id` directive is used for applications that don't support startup notification (console applications and some graphical applications).  The `-b` directive changes compton to run in the background.

## Set a background using `feh`
`feh` is a simple image viewer with the ability to set background images.  To set your wallpaper, run the following command in a terminal:

`feh --bg-scale path/to/image`

There are several other options for feh, including `--bg-fill`, `--bg-center`, `--bg-max`, and `--bg-tile`.

When you set a background with feh, it automatically creates a script at `$HOME/.fehbg`

To run this script on startup, automatically setting your wallpaper, add the following to your i3 config:

`exec sh ~/.fehbg`

## Start `nm-applet`
If you want to use `nm-applet` to manage your network connections, run the following command:

`exec --no-startup-id nm-applet &`

The `&` means that nm-applet will run in the background, rather than as a foreground process.  This can help prevent certain issues.

## Start `dunst`
`dunst` is a minimalistic notification daemon that can be easily configured.

`exec dunst &`
