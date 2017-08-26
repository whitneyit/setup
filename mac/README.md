# Setup Mac #

Download and install the following

 * [Alfred](http://www.alfredapp.com/#download "Download AlrfedApp")
 * [Dropbox](https://www.dropbox.com/downloading "Download Dropbox")
 * [iTerm2](http://www.iterm2.com/#/section/home "Download iTerm2")

Open up terminal and type

```bash
$ xcode-select --install
```

What this does is prompt to install the command line tools. If for whatever
reason, that does not work. You can manually download CLT from the Apple
website. To get there, open Xcode, and in the menubar go:

> Xcode > Open Developer Tool > More Developer Tools...

This should take you to the Apple website. Near the top of the page you should
find the most recent version of CLT.

## Configure ##

Whilst the CLT are downloading, there are a few settings that we can adjust in
the mean time. Open `System Preferences` and follow these [instructions](mac.config.md)

## Tools ##

Install [Dropbox](https://www.dropbox.com/downloading "Download Dropbox") and
follow any promps that may arise.

## Environment ##

### iTerm2 ###

Download the [Solarized](https://github.com/altercation/solarized/tree/master/iterm2-colors-solarized) colourscheme for iTerm2.

### NPM ###

If you have any problems installing npm, these steps may help

```bash
$ sudo chown -R "$(whoami)" ~/.npm
```

```bash
$ sudo chown -R "$(whoami)" /usr/local/lib/
```
