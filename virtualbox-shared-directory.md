# File sharing between host and Virtualbox guest

* In the Virtualbox Manager window, go into Settings of your guest machine.
* Select the shared folders section and add a new shared folder (a directory on the host machine)
* Do not forget to enable auto-mount
* In the host os, you have to add your user to the `vboxsf` group:
  `sudo gpasswd -a <username> vboxsf`
* Log out of the current session and log back in.
* Now you can access the shared directory which is mounted at `/media/sf_<foldername>`.

Source: https://www.linuxbabe.com/virtualbox/how-to-enable-file-sharing-between-host-and-virtualbox-guest-os
