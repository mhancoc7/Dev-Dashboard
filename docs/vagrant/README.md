# Vagrant Setup:

<img src="https://raw.githubusercontent.com/mhancoc7/Dev-Dashboard/master/docs/assets/vagrant-dashboard.png"/>

## Pre-requisites:

- [Vagrant](https://www.vagrantup.com/)
- [VirtualBox](https://www.virtualbox.org/)

## Installation/Usage:

- Add your SSH key to GitHub. [More info...](https://help.github.com/en/articles/about-ssh)

- Clone the Dev-Dashboard
  - `git clone git@github.com:mhancoc7/Dev-Dashboard.git Vagrant`

- Go into the Vagrant directory
  - `cd Vagrant`

- Configuration options are located in the [setup/config/build.conf](https://github.com/mhancoc7/Dev-Dashboard/blob/master/setup/config/build.conf) file
  - git_user = Your GitHub username
  - git_email = Your GitHub email
  - git_name = Your GitHub Name
  - git_array = An array of the repos from your GitHub account that you would like to include in your dashboard
  - db_password = The password to use for MariaDB and phpMyAdmin (The username is `phpmyadmin`)

- Run `bash build.sh`

- Dev Dashboard can be located via http://localhost:8080

- Use Vagrant commands to stop, start, and destroy Vagrant from the Vagrant directory. [More info...](https://www.vagrantup.com/docs/cli/)

When using the Vagrant setup your repos are cloned to your local machine under `localhost/www/html/` and are synced to the Vagrant box. This way you can destroy and recreate the Vagrant box without worrying about your code. 

If you want to add more projects after intial setup just add repos to the [setup/config/build.conf](https://github.com/mhancoc7/Dev-Dashboard/blob/master/setup/config/build.conf) file and re-run `bash build.sh` and they will show up in your dashboard.

The `Labs` section of the dashboard is there for tinkering with GitHub repos and other projects. So you can clone a GitHub repo manually into `localhost/www/html/*labs/` to test out the code. This section is not meant to be persistent but more of a sandbox.

# *Tips:*
- If you want to have custom icons in the dashboard list be sure that your repos have a `favicon.ico` or `favicon.png` in the root of the respective repo.

> #### `Note: All code is provided as-is without any warranty. Use at your own risk.`
