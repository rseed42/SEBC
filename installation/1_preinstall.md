## Swappiness

Checked default vm.swappiness config:

[root@ip-172-31-23-134 mysql-connector-java-5.1.40]# cat /proc/sys/vm/swappiness
30

-> Changing swappiness:

echo "vm.swappiness=1" >> /etc/sysctl.conf


-> Unable to set swappiness via /etc/sysctl.conf


## Mount options

One node example:

cat /etc/fstab

[root@ip-172-31-23-134 ~]# cat /etc/fstab

#
# /etc/fstab
# Created by anaconda on Mon Feb 22 17:08:22 2016
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=ef6ba050-6cdc-416a-9380-c14304d0d206 /                       xfs     defaults,noatime        0 0

-> Added noatime attribtue

Check mounts

[root@ip-172-31-23-134 ~]# mount |grep xvda
/dev/xvda1 on / type xfs (rw,noatime,seclabel,attr2,inode64,noquota)

[root@ip-172-31-25-204 ~]# mount |grep xvda
/dev/xvda1 on / type xfs (rw,noatime,seclabel,attr2,inode64,noquota)

[root@ip-172-31-22-145 ~]# mount |grep xvda
/dev/xvda1 on / type xfs (rw,noatime,seclabel,attr2,inode64,noquota)

[root@ip-172-31-18-1 ~]# mount |grep xvda
/dev/xvda1 on / type xfs (rw,noatime,seclabel,attr2,inode64,noquota)

[root@ip-172-31-28-101 ~]# mount |grep xvda
/dev/xvda1 on / type xfs (rw,noatime,seclabel,attr2,inode64,noquota)


## Reserved disk space

[root@ip-172-31-22-192 ~]# tune2fs -l /dev/xvde2 | grep "Reserved block count"
Reserved block count:     1572864

Tune the reserved space:

tune2fs -m 0 /dev/xvde2

- After tuning:

[root@ip-172-31-16-142 ~]# tune2fs -l /dev/xvde2 | grep "Reserved block count"
Reserved block count:     0

[root@ip-172-31-22-192 ~]# tune2fs -l /dev/xvde2 | grep "Reserved block count"
Reserved block count:     0

[root@ip-172-31-26-157 ~]# tune2fs -l /dev/xvde2 | grep "Reserved block count"
Reserved block count:     0

[root@ip-172-31-22-31 ~]# tune2fs -l /dev/xvde2 | grep "Reserved block count"
Reserved block count:     0


## Transparent hugepages

Turned off transparent hugepages

[centos@ip-172-31-23-134 ~]$ cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]

[root@ip-172-31-25-204 ~]# cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]

[root@ip-172-31-22-145 ~]# cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]

[root@ip-172-31-18-1 ~]# cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]

[root@ip-172-31-28-101 ~]# cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]


## nslookup

Install utilities:

yum install -y bind-utils

Updated /etc/hosts for easy access

54.157.150.141 master
54.204.195.169 edge
54.145.151.130 dn01
54.86.221.36 dn02
54.175.89.35 dn03

Lookup a host (test):

[root@ip-172-31-23-134 ~]# nslookup ec2-54-204-195-169.compute-1.amazonaws.com
Server:         172.31.0.2
Address:        172.31.0.2#53

Non-authoritative answer:
Name:   ec2-54-204-195-169.compute-1.amazonaws.com
Address: 172.31.25.204


[root@ip-172-31-23-134 ~]# getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
54.157.150.141  master
54.204.195.169  edge
54.145.151.130  dn01
54.86.221.36    dn02
54.175.89.35    dn03



[root@ip-172-31-16-142 ~]#

## network attributes

[root@ip-172-31-23-134 ~]# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.23.134  netmask 255.255.240.0  broadcast 172.31.31.255
        inet6 fe80::c58:3eff:fe3b:455c  prefixlen 64  scopeid 0x20<link>
        ether 0e:58:3e:3b:45:5c  txqueuelen 1000  (Ethernet)
        RX packets 171211  bytes 250039631 (238.4 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 74172  bytes 5046890 (4.8 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 6  bytes 416 (416.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6  bytes 416 (416.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

[root@ip-172-31-25-204 ~]# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.25.204  netmask 255.255.240.0  broadcast 172.31.31.255
        inet6 fe80::c62:90ff:fe75:1aa4  prefixlen 64  scopeid 0x20<link>
        ether 0e:62:90:75:1a:a4  txqueuelen 1000  (Ethernet)
        RX packets 1483  bytes 1086480 (1.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1428  bytes 128554 (125.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 6  bytes 416 (416.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6  bytes 416 (416.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

[root@ip-172-31-22-145 ~]# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.22.145  netmask 255.255.240.0  broadcast 172.31.31.255
        inet6 fe80::c31:9bff:fecc:6cb2  prefixlen 64  scopeid 0x20<link>
        ether 0e:31:9b:cc:6c:b2  txqueuelen 1000  (Ethernet)
        RX packets 1281  bytes 1067404 (1.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1282  bytes 107098 (104.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 6  bytes 416 (416.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6  bytes 416 (416.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

[root@ip-172-31-18-1 ~]# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.18.1  netmask 255.255.240.0  broadcast 172.31.31.255
        inet6 fe80::cbc:62ff:fe7e:742c  prefixlen 64  scopeid 0x20<link>
        ether 0e:bc:62:7e:74:2c  txqueuelen 1000  (Ethernet)
        RX packets 1202  bytes 1063287 (1.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1221  bytes 102096 (99.7 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 6  bytes 416 (416.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6  bytes 416 (416.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

[root@ip-172-31-28-101 ~]# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.28.101  netmask 255.255.240.0  broadcast 172.31.31.255
        inet6 fe80::ccb:c3ff:fe13:f658  prefixlen 64  scopeid 0x20<link>
        ether 0e:cb:c3:13:f6:58  txqueuelen 1000  (Ethernet)
        RX packets 1199  bytes 1063351 (1.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1218  bytes 101826 (99.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 6  bytes 416 (416.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6  bytes 416 (416.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



## nscd

Installed & configured nscd:

yum install -y nscd
chkconfig nscd on
service nscd start

service nscd status

[root@ip-172-31-23-134 ~]# service nscd status
Redirecting to /bin/systemctl status  nscd.service
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:31:34 UTC; 11min ago
 Main PID: 19426 (nscd)
   CGroup: /system.slice/nscd.service
           └─19426 /usr/sbin/nscd

[root@ip-172-31-25-204 ~]# service nscd status
Redirecting to /bin/systemctl status  nscd.service
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:47:26 UTC; 2min 0s ago
 Main PID: 9245 (nscd)
   CGroup: /system.slice/nscd.service
           └─9245 /usr/sbin/nscd

[root@ip-172-31-22-145 ~]# service nscd status
Redirecting to /bin/systemctl status  nscd.service
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:46:35 UTC; 3min 7s ago
 Main PID: 9194 (nscd)
   CGroup: /system.slice/nscd.service
           └─9194 /usr/sbin/nscd

[root@ip-172-31-18-1 ~]# service nscd status
Redirecting to /bin/systemctl status  nscd.service
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:49:10 UTC; 53s ago
  Process: 9186 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 9187 (nscd)
   CGroup: /system.slice/nscd.service
           └─9187 /usr/sbin/nscd

[root@ip-172-31-28-101 ~]# service nscd status
Redirecting to /bin/systemctl status  nscd.service
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:49:13 UTC; 1min 6s ago
  Process: 9178 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 9179 (nscd)
   CGroup: /system.slice/nscd.service
           └─9179 /usr/sbin/nscd
		   
	   



## ntpd [All nodes]

yum install -y ntp
chkconfig ntpd on
service ntpd start


service ntpd status


[root@ip-172-31-23-134 ~]# service ntpd status
Redirecting to /bin/systemctl status  ntpd.service
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:48:10 UTC; 5s ago
  Process: 7626 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 7627 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─7627 /usr/sbin/ntpd -u ntp:ntp -g

[root@ip-172-31-25-204 ~]# service ntpd status
Redirecting to /bin/systemctl status  ntpd.service
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:52:02 UTC; 3s ago
  Process: 9411 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 9412 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─9412 /usr/sbin/ntpd -u ntp:ntp -g
		   
[root@ip-172-31-22-145 ~]# service ntpd status
Redirecting to /bin/systemctl status  ntpd.service
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:52:08 UTC; 3s ago
  Process: 9341 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 9342 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─9342 /usr/sbin/ntpd -u ntp:ntp -g

[root@ip-172-31-18-1 ~]# service ntpd status
Redirecting to /bin/systemctl status  ntpd.service
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:52:14 UTC; 3s ago
  Process: 9293 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 9294 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─9294 /usr/sbin/ntpd -u ntp:ntp -g

[root@ip-172-31-28-101 ~]# service ntpd status
Redirecting to /bin/systemctl status  ntpd.service
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2016-11-15 12:52:20 UTC; 3s ago
  Process: 9280 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 9281 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─9281 /usr/sbin/ntpd -u ntp:ntp -g

		   
		   
		   
		   
