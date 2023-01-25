# Test-task-Bonding-LACP-Ubuntu-18

#root@tryit-legible:/etc/netplan# vi /etc/netplan/netconfig.yaml

```yml
network:
 version: 2
 renderer: networkd
 ethernets:
   ens18:
     dhcp4: no
     dhcp6: no
   ens19:
     dhcp4: no
 
       
 bonds:
   bond0:
     interfaces: [ens18, ens19]
     addresses: [192.168.2.2/22]
     gateway4: 192.168.2.1
     nameservers:
       search: [local]
       addresses: [8.8.8.8]
     parameters:
       mode: 802.3ad
       lacp-rate: fast
       mii-monitor-interval: 100
```
```bash
 root@tryit-legible:netplan try  
 root@tryit-legible:netplan apply 
 root@tryit-legible:reboot    
 ```      
 # Ubuntu Удалённая смена пароля пользователя
 ```bash
 root@tryit-legible: nano passwd.sh
 #!/bin/bash
 echo 'user:123456' | chpasswd
 root@tryit-legible: chmod +x passwd.sh
 ssh root@v1251486.hosted-by-vdsina.ru 'bash -s' < /home/user/psswd.sh
 ```

 # Ubuntu Создание пользователя с паролем
  ```bash
 root@tryit-legible: nano passwd.sh
 #!/bin/bash
 useradd user2
 echo 'user2:1234567' | chpasswd
 root@tryit-legible: chmod +x adduser.sh
 ssh root@v1251486.hosted-by-vdsina.ru 'bash -s' < /home/user/adduser.sh
 ```
 
 # Ubuntu Смена стандартного порта ssh
 ```bash
 root@tryit-legible: nano ssh.sh
 #!/bin/bash
 echo 'Port 2222' >> /etc/ssh/sshd_config
 systemctl restart sshd
 root@tryit-legible: chmod +x ssh.sh
 ssh root@v1251486.hosted-by-vdsina.ru 'bash -s' < /home/user/ssh.sh
 ssh root@v1251486.hosted-by-vdsina.ru -p 2222
 ```
 
 
