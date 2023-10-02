# Install_LEMP_STACK
Install_LEMP_STACK

**How to Install PHP-FPM with Nginx on Ubuntu**

Prerequisites
Have an Ubuntu 18.04 x64 / 19.10 x64 / 20.04 x64 instance.
Logged in as a root with sudo privileges.
Installed Nginx


**Step 1: Add Ondrej PHP PPA repository**
PHP can be installed using Ondřej Surý PPA, so install the software-properties-common package, add the ondrej PPA and update your sources using the following commands:

_sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ondrej/php
sudo apt update_

![image](https://github.com/ntnguyen147/Install_LEMP_STACK/assets/39340621/92a80a74-3166-4200-8b2e-2ec4787c2cea)

**
**Step 2: Install PHP 7.3-FPM/PHP 7.4-FPM For Nginx****
Install PHP 7.3-FPM on Ubuntu using the following command:

_sudo apt install php7.3-fpm_

or
_sudo apt install php7.4-fpm_

![image](https://github.com/ntnguyen147/Install_LEMP_STACK/assets/39340621/1e640373-7ae0-40e1-a437-3a9a2243342a)
**
**Step 3: Check the PHP installation****
You can use** php -v** the command to check the PHP version installed on your server and output will be


PHP 7.3.11-1+ubuntu19.10.1+deb.sury.org+6 (cli) (built: Oct 28 2019 21:34:37) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.11, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.3.11-1+ubuntu19.10.1+deb.sury.org+6, Copyright (c) 1999-2018, by Zend Technologies

In case if you have installed PHP 7.4-FPM, following will be output:


PHP 7.4.28 (cli) (built: Feb 17 2022 16:06:35) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
    with Zend OPcache v7.4.28, Copyright (c), by Zend Technologies

![image](https://github.com/ntnguyen147/Install_LEMP_STACK/assets/39340621/bbac64d0-30f1-4078-9535-8f714cc24fd1)

**Step 4: Install PHP Extensions**
Install the most commonly used PHP extensions using the following command for PHP 7.3:

_sudo apt install php7.3-common php7.3-zip php7.3-curl php7.3-xml php7.3-xmlrpc php7.3-json php7.3-mysql php7.3-pdo php7.3-gd php7.3-imagick php7.3-ldap php7.3-imap php7.3-mbstring php7.3-intl php7.3-cli php7.3-tidy php7.3-bcmath php7.3-opcache
or for PHP 7.4, run the following one._

_
sudo apt install php7.4-common php7.4-zip php7.4-curl php7.4-xml php7.4-xmlrpc php7.4-json php7.4-mysql php7.4-pdo php7.4-gd php7.4-imagick php7.4-ldap php7.4-imap php7.4-mbstring php7.4-intl php7.4-cli php7.4-tidy php7.4-bcmath php7.4-opcache_

You can confirm the installed version of any PHP extension using apt policy command i.e. apt policy php7.3-cli and output will be


php7.3-cli:
  Installed: 7.3.11-1+ubuntu19.10.1+deb.sury.org+6
  Candidate: 7.3.11-1+ubuntu19.10.1+deb.sury.org+6
  Version table:
 *** 7.3.11-1+ubuntu19.10.1+deb.sury.org+6 500
        500 http://ppa.launchpad.net/ondrej/php/ubuntu eoan/main amd64 Packages
        100 /var/lib/dpkg/status
     7.3.11-0ubuntu0.19.10.1 500
        500 http://archive.ubuntu.com/ubuntu eoan-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu eoan-security/main amd64 Packages
     7.3.8-1 500
        500 http://archive.ubuntu.com/ubuntu eoan/main amd64 Packages
Now, PHP 7.3-FPM has been installed on your Ubuntu server.

![image](https://github.com/ntnguyen147/Install_LEMP_STACK/assets/39340621/6b493c79-ab91-4bd8-8401-374c40cf278d)
**
**
Step 5: Configure PHP 7.3-FPM/PHP 7.4-FPM****
The default PHP configuration file is at **/etc/php/7.3/fpm/php.ini** or **/etc/php/7.4/fpm/php.ini** and if we want to modify the default PHP configuration, open file by using the following command:

_sudo nano /etc/php/7.3/fpm/php.ini
or
sudo nano /etc/php/7.4/fpm/php.ini_
Make the changes on the following below lines in opened file and save. Below are recommended values being great settings to apply in your environments.


_max_execution_time = 180
max_input_time = 360
max_input_vars = 5000
memory_limit = 256M
cgi.fix_pathinfo = 0
file_uploads = On
post_max_size = 192M
upload_max_filesize = 96M
allow_url_fopen = On_


After making the change above, save the file and close out.

Step 6: Restart PHP-FPM and Nginx
After installing PHP and related modules, all you have to do is restart PHP-FPM and Nginx to reload PHP configurations.

To restart Nginx and PHP-FPM, run the commands below
__
**sudo php-fpm7.3 -t
sudo systemctl restart php7.3-fpm
sudo systemctl restart nginx_**
_
or

sudo php-fpm7.4 -t
sudo systemctl restart php7.4-fpm
sudo systemctl restart nginx
