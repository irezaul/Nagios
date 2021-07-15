# Nagios - `Monitoring Tool`

### CICD- Countinuous Integration & Continuous Deployment

`Countinuous Integration`
Countinuous Integration  |  BY 
| :--- | ---: 
Planning  |  Jira 
Coding  | git
Build   | Maven 
Testing | Selenium

`Continuous Deployment or Continuous Delivery`
Continuous Deployment  |  BY 
| :--- | ---: 
Deployment is 2 types | 1. Treditional deployment 2. Containerized deployment
Treditional| puppet or Ansible  | ----
Containerized deployment | Docker/ Kubernetes

`Countinuous Monitoring`

Monitoring  |  BY 
| :--- | ---: 
Monitoring  | Nagios |
 
 
 #### 1. Update Apt
 ```bash
 apt-get update
 ```
 #### 2. Install Nagios & dependencies
 ```bash
 apt-get update && apt-get install build-essential apache2 php openssl perl make php-gd libgd-dev libapache2-mod-php libperl-dev libssl-dev deamon wget apache2-utlis unzip
```
### On VM-Machine use this command
```bash
apt-get update && apt install -y autoconf bc gawk dc build-essential gcc libc6 make wget unzip apache2 php libapache2-mod-php libgd-dev libmcrcd ypt-dev make libssl-dev snmp libnet-snmp-perl gettext
```
### `also we can install one by one`
``` bash
apt-get install build-essential

apt-get install apache2

apt-get install php

apt-get install openssl

apt-get install perl

apt-get install make

apt-get install php-gd

apt-get install libgd-dev

apt-get install libapache2-mod-php

apt-get install libperl-dev

apt-get install libssl-dev

sudo apt install librecad

sudo apt-get install daemon

apt-get install wget

apt-get install  apache2-utils

apt-get install  unzip

```
#### 3. Check if Apache is installed in Nagios Server by pasting public IP or static IP into the web browser.
> Create nagios user and nagcmd group and add the nagios and apache user to the part of the nagcmd group.
```bash
useradd nagios
groupadd nagcmd
usermod -a -G nagcmd nagios
usermod -a -G nagcmd www-data
```
### 4. Nagios Installation (cont)
#### Install `Nagios Core`
```bash
cd /tmp 
wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.4.6.tar.gz
tar -zxvf /tmp/nagios-4.4.6.tar.gz
cd /tmp/nagios-4.4.6/
```
#### 5. Perform the below steps to compile the Nagios from the source code
```bash
./configure --with-nagios-group=nagios --with-command-group=nagcmd --with-httpd_conf=/etc/apache2/sites-enabled/
make all
make install
make install-init
make install-config
make install-commandmode
```
#### 6. Execute the below command in the terminal to install Nagios web interface
```bash
make install-webconf
```
#### 7. Create Nagios Login and Password (use “nagios” as password)
```bash
htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin
```
#### 8. Run the following command: 
```bash
a2enmod cgi
```
#### 9. Restart Apache Service to make the new settings take effect
```bash
systemctl restart apache2.service
```
### Nagios Installation (cont)
#### 10. In web `browser` type: <server public-ip/nagios> like- `192.168.x.x/nagios` Click Hosts and you will see an error. This is because Nagios plugins has not been installed yet. Install Nagios plugins:
```bash
cd /tmp
wget https://nagios-plugins.org/download/nagios-plugins-2.3.3.tar.gz
tar -zxvf /tmp/nagios-plugins-2.3.3.tar.gz
cd /tmp/nagios-plugins-2.3.3/
```
#### 11. Compile and install the plugins
```bash
./configure --with-nagios-user=nagios --with-nagios-group=nagios
make
make install
```

#### 12. Verify the sample Nagios configuration files. You should have “0” warnings and errors
```bash
/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg
```
#### 13. Enable Nagios to start automatically at system startup and start Nagios service
```bash
systemctl enable nagios
systemctl start nagios
```
> Your localhost on Nagios dashboard should be up and services should come up
### * Nagios `File System`
![Screenshot 2021-07-15 at 8 29 12 PM](https://user-images.githubusercontent.com/77927449/125805296-2197a051-6e9f-4cbf-b835-e567fff1d7f5.png)
#### * Nagios File System (cont)
> Nagios is installed under directory `/usr/local/nagios/`
![nagios file system](https://user-images.githubusercontent.com/77927449/125806734-1fccbdc3-f005-4207-8ee7-a613fb5ab3ba.png)

> Under this directory libexec contain all the plugins as binary files. By default there are total 50 plus plugins installed
![50 File system](https://user-images.githubusercontent.com/77927449/125811711-8af25c1d-89e4-4073-8e06-f0887196c86f.png)

> The etc directory is the main operational directory and contain nagios.cfg file and objects directory `/usr/local/nagios/etc/objects/`
![object](https://user-images.githubusercontent.com/77927449/125817605-5c4f4af4-824f-4505-80f3-79a8c74869f5.png)

> All the object resources in Nagios are defined inside the nagios.cfg file. This file determines what kind of resource/objects can be declared on the dashboard which can be external servers (linux/windows), log files, printers, routers, switches etc
![nagios_cfg](https://user-images.githubusercontent.com/77927449/125818409-2ed42844-42b9-4921-8372-898c4d4cc1ab.png)




