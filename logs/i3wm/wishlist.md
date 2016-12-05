Things I need out of i3wm
=========================

1. A GNOME "compose key" equivalent
    * The compose key is helpful in GNOME to type symbols and my ever-favorite ellipse character. However, it's unclear how to replicate this functionality in i3wm. Will investigate.
2. Syncing with Dropbox daemon
    * On first observation, it's unclear if i3wm is properly syncing with Dropbox. Based on the [Fedora Magazine](https://fedoramagazine.org/getting-started-i3-window-manager/) article, I added a line that should start the daemon at start.
    * `exec --no-startup-id dropbox start`
3. Screencloud support (needs a dock)
    * Whether there even is a solution to this is unclear. It might be better to write a script that uploads an image to my own server or to Imgur, and bind that to a key combination. This is a pesky problem to resolve...