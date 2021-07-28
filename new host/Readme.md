### How to crete a new Monitoring your laptop your mobile & your web..

#### 1. Install nagios & all dependencies & run also ipaddress/nagios
> then config the file go to the `/usr/local/nagios/etc/` folder & create a new folder `servers`
> create a new file name is - `host.cfg`
> open with a editor
> write here the name / ip and other option - 

```bash
define host{
        use                        linux-server
        host_name                  my_hostpc
        alias                      Macbook_pro
        address                    192.168.1.11
        max_check_attempts         3
        check_period               24x7
        notification_interval      30
        notification_period        24x7
}

define host{
        use                        linux-server
        host_name                  My_Phone
        alias                      Samsung_M01s
        address                    192.168.1.7
        max_check_attempts         3
        check_period               24x7
        notification_interval      30
        notification_period        24x7
}
```
![write the code](https://user-images.githubusercontent.com/77927449/127211034-94b43312-d321-496e-a73d-a2c51f3d39d9.png)

> save it & wait for the service up

![up_successfully](https://github.com/irezaul/Nagios/blob/main/new%20host/Nagios%20ip%20up.png)

> check on router attach devices..

![attach_devices](https://user-images.githubusercontent.com/77927449/127211774-7767d7cc-2297-496f-bfe9-42b178794f16.png)

> also check mobile ip

![mobile_ip_up](https://github.com/irezaul/Nagios/blob/main/new%20host/nagios%20mobile%20ip%20.png)

