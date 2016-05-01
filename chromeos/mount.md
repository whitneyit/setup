To mount the chromeos disk for writing open up a shell and write

```sh
$ sudo /usr/share/vboot/bin/make_dev_ssd.sh --remove_rootfs_verification
```

After that has completed, reboot your machine and get back into a shell.

Now we're going to make a script to enable write access when we need it:

```sh
$ vim /sbin/rw
```

Paste the following into the file:

> #!/bin/bash
> sudo mount -o remount,rw /
> sudo mount -o remount,exec /mnt/stateful_partition
> sudo mount -i -o remount,exec /home/chronos/user

Now when you need write access just run:

```sh
$ sudo rw
```
