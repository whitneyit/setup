# Setup ChromeOS

First we need to enable [developer mode](http://www.howtogeek.com/210817/how-to-enable-developer-mode-on-your-chromebook)

With that done, we can access the hidden ChromeOS shell.

Open up Chrome and press `Ctrl+Alt+T` then type `shell`.

You should see something like this:

![shell](http://i.imgur.com/UmzgMXq.png)

===

Next, we need to configure the update channel, but first we need an elevated shell. To do that, we need to type:

```sh
$ sudo su
```

You may get some warning about using [sudo](https://en.wikipedia.org/wiki/Sudo) don't worry about it, that's normal.

If you are asked for a password, you can try fixing that [here](passwd.md).

Once you're logged in as root, you should see something like this

![sudo_shell](http://i.imgur.com/eHdSiXD.png)

We can now set the update channell with the following.

```sh
$ update_engine_client --channel=canary-channel --update
```

Now you have to wait for the patch to be downloaded. Once it has been, you'll get a notification to perform a
[PowerWash](https://support.google.com/chromebook/answer/183084)
to update to the canary channel.

Once you've powerwashed the device, you'll need to re-enable
[developer mode](http://www.howtogeek.com/210817/how-to-enable-developer-mode-on-your-chromebook).

===

Now we're going to download
[crouton](https://github.com/dnschneid/crouton) from [here](https://goo.gl/fd3zc).

Once that has been downloaded open a terminal as described above, then type:

```sh
$ shell
```

This will start a regular shell. Now we can run:

```sh
$ sudo sh ~/Downloads/crouton -r trusty -t audio,chrome-dev,cli-extra,keyboard,touch,unity,xorg
```

Grab a coffee as the above command will take a while. Once that has finished, you can log into the shell with:

```sh
$ sudo enter-chroot
```

Congrats! You just setup a Ubuntu on your Chromebook.

===

To configure the environment first we need to do a few things.

Install our dependencies

```sh
$ sudo apt-get install -y curl git
```

Setup dotfiles

```sh
$ mkdir -p ~/Code/dotfiles
$ cd ~/Code/dotfiles
$ bash -c "$(curl -fsSL https://raw.github.com/whitneyit/dotfiles/master/bin/dotfiles)"
```

Create ssh keys

```sh
$ mkdir -p ~/Code/ssh
$ cd ~/Code/ssh
$ bash -c "$(curl -fsSL https://raw.github.com/whitneyit/ssh/master/setup)"
```

Copy those keys to the `~/Downloads` folder:

```sh
$ cp ~/.ssh/*.pub ~/Downloads
```

Next, we need to open them in an editor. You can install
[Simple Editor](https://chrome.google.com/webstore/detail/simple-editor/dbcakhkjkfomilmicpakkdfoannfonmi)
which is pretty good.

Once they're open, copy and paste them into the various sites that require keys:

* [GitHub](https://github.com/settings/keys),
* [BitBucket](https://bitbucket.org/account/user/whitneyit/ssh-keys/)
* [DigitalOcean](https://cloud.digitalocean.com/settings/security)

===

If at any time you want to delete the `chroot` simple bring up the Chrome shell and run:

```sh
$ sudo delete-chroot trusty
```

===

If you want to mount the filesystem, you can view the instructions [here](mount.md).
