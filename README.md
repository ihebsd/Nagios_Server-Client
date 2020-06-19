# Nagios_Server-Client
Configuration of Nagios Server &amp; Client Centos 7

### :speech_balloon: Introduction
Nagios is an application for system and network monitoring. It monitors the specified hosts and services, alerting when systems have malfunctions and when they return to normal operation. It is free software under the GPL license.

## :gear: Configuration 

Modify config file to the client to be monitored:

```shell
$ vi /usr/local/nagios/etc/servers/clients.cfg
```
Add the following lines:

```shell
define host{

use                             linux-server

host_name                       client

alias                           client

address                         @Client_IP

max_check_attempts              5

check_period                    24x7

notification_interval           30

notification_period             24x7

}
```
Here, @IP_Client_Adress is my nagios client IP address. Finally restart nagios service.

```shell
systemctl restart nagios
```
Edit /etc/nagios/nrpe.cfg file,
```shell
sudo vi /etc/nagios/nrpe.cfg
```
Add your Nagios server ip address:

Find the following line and add the Nagios server IP
```shell
allowed_hosts=127.0.0.1 @IP_Nagios_Server
```

### Reviewing the prediction results :sparkles:	
<p align="center">
  <img src="https://user-images.githubusercontent.com/47121168/85165507-3d1de880-b266-11ea-85dd-fd9f091cf856.PNG" width="600"/> 
</p>
