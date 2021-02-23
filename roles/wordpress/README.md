# Introduction

This playbook installs WordPress environment with following features:

  - wp-otp plugin : time based one time password authenticaiton
  - companion-auto-update plugin : updates all components background
  - ssh-sftp-updater-support plugin : add SSH2 support to update feature in administration screen


Follow the prerequisite section of [this repository's top page](https://github.com/hotta/ansible-centos8). Then run:

```bash
ansible-playbook jobs/wordpress.yml
```

If the command went well, add "wordpress.local" host entry to your mother OS's hosts file.

```bash
192.168.56.2    wordpress.local
```

The IP address above is the one you specified as "private_network" in Vagrantfile. Then visit http://wordpress.local and you will see the WordPress's default top page.

## OPT configuration

Visit http://wordpress.local/wp-admin/ and you will see login page.

![Screenshot](https://github.com/hotta/images/blob/master/wp-login.png?raw=true) 
There already be the OTP input area but it is disabled by default. Input user id and password defined as WP_ADMIN_USER / WP_ADMINPASS in group_vars/all or host_vars/localhost.yml (if any). Login as the administrator, then select "Edit Profile" in "Hello (YOURNAME)" at the top right.

![Screenshot](https://github.com/hotta/images/blob/master/wp-otp-set.PNG?raw=true)

You will see the OTP settings at the middle of screen. If you don't have already installed the Authentication App in your smart phone, install it first. Then read the QR code displayed on screen using ther app, the wordpress site will be registered in the app. Input the six digit code into the admin console so that OTP is enabled.
