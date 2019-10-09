# Pi Zero Setup:

<img src="https://raw.githubusercontent.com/mhancoc7/Dev-Dashboard/master/docs/assets/pizero-dashboard.png"/>

The Pi Zero installation is designed to work with a Pi Zero setup as a USB dongle. This is a more advanced setup and may not be useful to many. More info on how a Pi Zero USB dongle can be setup can be found on my [Pi Lab blog](https://pilab.dev/raspberry-pi-portable-dev-server).

Once you have a working Pi Zero USB dongle built you can use the steps below to fully set up the Pi Zero as a portable dev server. This setup assumes that you will be using the Pi Zero in a similar fashion to Vagrant. In other words don't run this on a Pi Zero where you have other things setup. The idea here is to use the Pi Zero as a dev server that can easily be rebuilt using this script.

- Flash Raspbian to SD card using [Etcher](https://www.balena.io/etcher/)

- Once flashing is complete remove and reinsert SD card. This should auto mount two directories.

- Open the "boot" directory and Put `dtoverlay=dwc2` at the end of the config.txt

- Open the "boot" directory and  Put `modules-load=dwc2,g_ether` right after `rootwait` in the cmdline.txt

- Copy the contents of "pre-setup/boot" from the this project into the boot directory

- Modify the "wpa_supplicant.conf" file that you copied into the boot directory with your WiFi creds

- Unmount the SD card and remove from laptop

- Insert SD card into Pi Zero

- Plug Pi Zero USB dongle into laptop

- SSH into pi using `ssh pi@raspberrypi.local` with the default pi password

- Add the pi's ssh key to GitHub. [More info...](https://help.github.com/en/articles/about-ssh)

- Clone Dev-Dashboard `git clone git@github.com:mhancoc7/Dev-Dashboard.git`

- Go into the Dev-Dashboard directory `cd Dev-Dashboard`

- Configuration options are located in the `setup/build.conf` directory.
  - git_user = Your GitHub username.
  - git_array = An array of the repos from your GitHub account that you would like to include in your dashboard.
  - pi_password = The password that you would like to use on the Pi Zero. The default is to keep the default pi password.
  - timezone = The timezone to set the Pi Zero to.
  - locales = The locales to use on the Pi Zero.

- The MariaDB password can be set on line 4 of the `setup/bootstrap` file.

- Run `bash build.sh`

(Options: Use '-hn <hostname>' to choose hostname. If you do not specify a hostname `pizero.local` will be used.)

- The build.sh script will reboot the Pi Zero at the end

- Dev Dashboard can be accessed via http://pizero.local or whatever hostname you set using the '-hn' flag

- You can ssh into the Pi Zero using `ssh pi@pizero.local` or whatever hostname you set using the '-hn' flag

- Add your laptop's SSH Key to Pi Zero `ssh-copy-id pi@pizero.local` or whatever hostname you set using the '-hn' flag to make it easier to login

If you want to add more projects after intial setup you can either add repos to the `setup/build.conf` file and re-run `bash build.sh` or manually clone repos into the `/var/www/html/` directory on the pi and they should show up in your dashboard.

The `Labs` section of the dashboard is there for tinkering with GitHub repos and other projects. So you can clone a GitHub repo manually into `/var/www/html` to test out some code. This section is not meant to be persistent but more of a sandbox.