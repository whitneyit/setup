If you were asked for a password when writing `sudo su` this document can help you.

First exist the sudo prompt by pressing `Ctrl+D`, afterwards close the terminal.

Once the terminal is closed, press `Ctrl+Alt+F2`.

When it asks for a login type `root` and press enter. If the password is not empty, try one of the following:

* root
* toor
* chronos
* chrome
* chromium
* facepunch

That should log you in as root, if not, you're shit out of luck.

You can now change the password for the `chronos` user. To do so type `chromeos-setdevpasswd` and set it to `root`.

This means that from now on, if you type `sudo` whilst in a shell, you be prompted for a password of `root`.
