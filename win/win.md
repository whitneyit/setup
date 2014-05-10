Setup Windows
=============

```
Install the regs
```

```
Install the desktop theme.
```

Use this like for [Chrome](https://www.google.com/intl/en_au/chrome/browser/),
otherwise you'll get the UK version. Sign in to Chrome and it'll start to
download and install your extensions. Go through any plugin setup tabs that pop
up.

Install [Chocolatey](http://chocolatey.org)

Once installed use `Take Ownership` on the directory

Install [EditorConfig](http://chocolatey.org/packages/editorconfig.core)

To make `EditorConfig` work with Cygwin

```
cp /cygdrive/c/Chocolatey/bin/editorconfig ~/
dos2unix ~/editorconfig
mv ~/editorconfig /cygdrive/c/Chocolatey/bin/
```

```
Remove IE from the startbar.
```

```
Delete the contents of C:\Users\%USERNAME%\Favorites\
```

```
Press "Start" and type "Change background and colours on start", change the
colour settings to "orange/dragon"
```

```
Open Explorer, and in the url bar, type "Recycle Bin". Drag the bin icon into
the Favourites menu
```

```
Open Explorer, and in the sidebar, remove the "Recent Places" shortcut from the
"Favourites" menu.
```

```
Open Explorer, and in the sidebar, remove the "Recent Places" shortcut from the
"Favourites" menu.
```

```
Navigate to "C:\Users\" and drag your username to the "Favourites" menu.
```

Press "Start" and type `Disk management`

Click on the C drive segmant on `Disk 0`

In the Action menu, click `Create VHD`

Name it `FileHistory` and store it at `C:\`

In the `Virtual hard disk size` option, select 64 GB

This will take a while so be patient. Like 30 mins?

Right click on `Disk 1`

Select Initialise Disk and choose the MBR format

Right click the unallocated space and choose `New Simple Volume...`

Hit `Next` twice and change the drive letter to `Z`

Give the drive a `Volume Label of "File History"

Press "Start" and type "File History Settings"

Enable File History and select the Z drive

Hit the "Back up now" button if it isn't already going

Open Explorer and in the url bar type "Libraries"

On the page that spawns, right click and select "New > Library"

Name this library "Backup"

Install Office
==============

Navigate to the [office website](https://office.microsoft.com/en-au/MyAccount.aspx) and click the green install button to get a setup file

When OneNote is installed, you can remove the send to one note tool with these
options.

```
File > Options > Display > Place OneNote... uncheck
```

Next set up outlook

Download the following programs
===============================

Filezila
--------
https://filezilla-project.org/download.php?show_all=1

Dropbox
-------
https://dropbox.com/downloading

Creative Cloud
--------------
https://creative.adobe.com/products/creative-cloud

Node JS
------
http://nodejs.org

Git
---
http://git-scm.com/download/win

Cygwin
------
http://cygwin.com/setup-x86.exe (never x64)

Skype
-----
http://www.skype.com/en/download-skype/skype-for-windows/downloading/

Vagrant
-------
https://www.vagrantup.com/downloads.html

Virtual Box
-----------
https://www.virtualbox.org/wiki/Downloads

FileZilla setup
==============

Install FileZilla, uncheck "Language files" and "Shell Extension"

Vagrant setup
=============

If you want Vagrant to work in cygwin, you need to install it in C:\HashiCorp.
Vagrant will not work if it is installed into a folder with spaces in its name
because of this bug [#3308](https://github.com/mitchellh/vagrant/issues/3308).

Skype setup
===========

Press "Start" and click the down arrow in the bottom left hand corner. Type Skype and
if you see skype pop up, right click it, and from the bottom menu, choose uninstall

Next, Install the version of Skype that you just downloaded. Open the settings menu
by pressing "Ctrl+," and apply the following settings

	General
		* General settings
			[Y] When I double-click on a contact start a call
			[N] Show me as away...
			[Y] Start Skype when I start Windows
			[Y] Show profile pictures in Contact List

			[Change your picture]

		* Skype WiFi
			[N] Enable Skype WiFi

	Privacy
		* Privacy settings
			[N] Allow my online status to be shown on the web
			[N] Accept Skype browser cookies
			[N] Allow Microsoft targeted ads

	Notifications
		* Alerts
			[N] Help and Skype tips
			[N] Promotions

	IM & SMS
		* IM Settings
			[Y] Only allow people in my Contact list to send me instant messages

			[Show advanced settings]

			[Save all files to] Skydive\Skype


	Advanced
		* Advanced settings
			[N] Use Skype callto:
			[N] Use Skype tel:
			[N] Keep Skype in the taskbar whilst I'm signed in
			[N] Show Skype watermark during calls
			[N] Help improve Skype...

Git setup
=========

Keep hitting "Next" until you get to the components window.

Uncheck: "Windows Explorer Intergration"
Uncheck: "Associate .sh files to be run with Bash"
Check:   "Use a TrueType font in all console windows"

In the PATH environment settings

Check: "Run Git from the windows Command Prompt"

Line ending conversions

Check: "Checkout as-is, commit as-is"

Environment setup
=================

Open up "Command Prompt" by pressing "Start" and typing "cmd". Enter this;

```
mkdir C:\Users\%USERNAME%\Code\
```
```
mkdir C:\Users\%USERNAME%\Documents\Cygwin\
```
mkdir C:\Users\%USERNAME%\Documents\Cygwin\install\
```
```
mkdir C:\Users\%USERNAME%\Documents\Cygwin\packages\
```

Navigate the the `Cygwin` folde and select "Inlude in library > Backup"

Copy the cygwin `setup.exe` to
```
C:\Users\%USERNAME%\Documents\Cygwin\
```

Run the exe file and select **Install from Internet**

Now set the root directory to
```
C:\Users\-- USERNAME WITHOUT SUB --\Documents\Cygwin\install\
```

And then set the local packages dir to
```
C:\Users\-- USERNAME WITHOUT SUB --\Documents\Cygwin\packages\
```

Set the Internet connection **Direct Connection**

Select any of the mirrors, I just choose the top one;

```
mirrors.163.com
```

And when asked to select packages, choose packages from the following categories;

    Base
        * dos2unix

    Devel
        * gettext
        * git
        * git-completion

    Editors
        * Vi IMproved

    Libs
        * libsasl2

    Net
        * curl
        * openssh
        * openssl
        * rsync

    Utils
        * cygwin_utils
        * ncurses
        * tree

    Web
         * wget

Click next to finalise the install

Once that is complete, start up cygwin, wait for it to do its init step then
close it.

Next stat up cmd.exe as an admin and type the following
```
rmdir /s /q C:\Users\%USERNAME%\Documents\cygwin\install\home\%USERNAME%
```
```
mklink /D C:\Users\%USERNAME%\Documents\cygwin\install\home\%USERNAME% C:\Users\%USERNAME%
```

Here you have a choice as to where you want to store the codebase for the [dotfiles](https://github.com/whitneyit/dotfiles) repo. You can nabigate to any folder and store the codebase there or simply run this command from your home directory to have the code moved to a `.dotfiles` directory.

Open up Cygwin. I like to keep my dotfiles here.

```
$ mkdir -p ~/Code/dotfiles && cd ~/Code/dotfiles
```

```
$ bash -c "$(curl -fsSL raw.github.com/whitneyit/dotfiles/master/bin/dotfiles)"
```

Afterwards, navigate to the directory in which you installed the dotfiles repo,
and then navigate to `./shell/fonts/consolas` and `right click > install` the required fonts

Once that is complete, restart and you're good to go!!

SSH Setup
========

You may have already got a warning about a missing file in the `~/.ssh`, well we're fixing
that right now.

```
$ git clone https://github.com/whitneyit/ssh.git ~/Code/ssh
$ ln -fs ~/Code/ssh ~/.ssh
```

cygwin
chgrp -R Users ~/Code/ssh
chgrp -R Users ~/.ssh

chmod 700 ~/Code/ssh
chmod 700 ~/.ssh

The following files need a chmod of 600:

	config
	known_hosts
	any other ssh key

https://help.github.com/articles/generating-ssh-keys

```
$ git clone https://github.com/whitneyit/ssh.git
