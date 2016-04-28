# Setting up a Chromebook for development

First we need to enable [developer mode](http://www.howtogeek.com/210817/how-to-enable-developer-mode-on-your-chromebook)

With that done we can download [crouton](https://goo.gl/fd3zc)

Open up terminal

> Open Chrome and press `Ctrl+Alt+T` then type shell

To access an elevated shell:

```sh
$ sudo su
```

Next, configure the update channel

```sh
$ update_engine_client --channel=canary-channel --update
```

Now you have to wait for the patch to be downloaded. Once it has been, you'll get a notification to perform a
[PowerWash](https://support.google.com/chromebook/answer/183084)
to update to the canary channel.

Now we're going to download
[crouton](https://github.com/dnschneid/crouton).

Once that has been downloaded open a terminal as described above, then type:

```sh
$ shell
```

This will start a regular shell. Now we can run:

```sh
$ sudo sh ~/Downloads/crouton -r trusty -t audio,chrome-dev,cli-extra,keyboard,touch,unity,xorg
```

Grab a coffee as the above command will take a while. Once that has finished, log out of the shell `Ctrl+D` and then log back in with:

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

Copy those keys to the `~/Downloads` folder and open them in [Text](https://chrome.google.com/webstore/detail/text/mmfbcljfglbokpmkimbfghdkjmjhdgbg?hl=en)
and copy and paste them into
[GitHub](https://github.com/settings/keys),
[BitBucket](https://bitbucket.org/account/user/whitneyit/ssh-keys/)
etc.

===

If at any time you want to delete the `chroot` simple bring up the Chrome shell and run:

```sh
$ sudo delete-chroot trusty
```
