## Setup

### Basic Info

* OS: RHEL-6.5_GA_HVM-20140929-x86_64-11-Hourly2-GP2
* AMI: ami-00a11e68
* Region: US East (N. Virginia)
* Number of Machines: US East (N. Virginia)

List of nodes:

* Master:	ip-172-31-1-36.ec2.internal 52.23.185.95
* Node: 01 ip-172-31-1-32.ec2.internal 54.174.94.22
* Node: 02 ip-172-31-1-34.ec2.internal 54.88.95.178
* Node: 03 ip-172-31-1-33.ec2.internal 54.144.221.187
* Node: 04 ip-172-31-1-35.ec2.internal 54.174.131.153


### Disk Space 

```
[ec2-user@ip-172-31-1-36 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      126G  2.0G  118G   2% /
tmpfs           7.3G     0  7.3G   0% /dev/shm
```
```
[ec2-user@ip-172-31-1-32 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      126G  2.0G  118G   2% /
tmpfs           7.3G     0  7.3G   0% /dev/shm
```
```
[ec2-user@ip-172-31-1-34 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      126G  2.0G  118G   2% /
tmpfs           7.3G     0  7.3G   0% /dev/shm
```
```
[ec2-user@ip-172-31-1-33 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      126G  2.0G  118G   2% /
tmpfs           7.3G     0  7.3G   0% /dev/shm
```
```
[ec2-user@ip-172-31-1-35 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      126G  2.0G  118G   2% /
tmpfs           7.3G     0  7.3G   0% /dev/shm
```

### List of yum repos

```
[ec2-user@ip-172-31-1-36 ~]$ yum repolist enabled
Loaded plugins: amazon-id, rhui-lb, security
Repo rhui-REGION-client-config-server-6 forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-client-config-server-6 forced skip_if_unavailable=True due to: /etc/pki/rhui/product/rhui-client-config-server-6.crt
Repo rhui-REGION-client-config-server-6 forced skip_if_unavailable=True due to: /etc/pki/rhui/rhui-client-config-server-6.key
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel6.crt
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel6.key
Repo rhui-REGION-rhel-server-releases-optional forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-releases-optional forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel6.crt
Repo rhui-REGION-rhel-server-releases-optional forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel6.key
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel6.crt
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel6.key
Could not contact CDS load balancer rhui2-cds01.us-east-1.aws.ce.redhat.com, trying others.


Could not contact any CDS load balancers: rhui2-cds01.us-east-1.aws.ce.redhat.com, rhui2-cds02.us-east-1.aws.ce.redhat.com.
```


### Added users 

```
useradd -u 2700 bavaria
useradd -u 2800 saxony
groupadd democratic
groupadd social
usermod -a -G democratic saxony
usermod -a -G social bavaria
```

Check

```
[root@ip-172-31-1-36 ~]# id bavaria
uid=2700(bavaria) gid=2700(bavaria) groups=2700(bavaria),2802(social)

[root@ip-172-31-1-36 ~]# id saxony
uid=2800(saxony) gid=2800(saxony) groups=2800(saxony),2801(democratic)

[root@ip-172-31-1-36 ~]# grep bavaria /etc/passwd
bavaria:x:2700:2700::/home/bavaria:/bin/bash

[root@ip-172-31-1-36 ~]# grep saxony /etc/passwd
saxony:x:2800:2800::/home/saxony:/bin/bash

[root@ip-172-31-1-36 ~]# grep democratic /etc/group
democratic:x:2801:saxony

[root@ip-172-31-1-36 ~]# grep social /etc/group
social:x:2802:bavaria
```

### Tweak OS settings


#### Swappiness

Check
```
[root@ip-172-31-1-36 ~]# cat /proc/sys/vm/swappiness
60
```

Set
```
echo 'vm.swappiness = 1' >> /etc/sysctl.conf
```


Check again (after reboot later)
```
[ec2-user@ip-172-31-1-36 ~]$ cat /proc/sys/vm/swappiness
1

```

#### Transparent Hugepages

Check
```
cat /sys/kernel/mm/transparent_hugepage/enabled
[always] madvise never
```
Add in /etc/rc.local:
```
echo never > /sys/kernel/mm/transparent_hugepage/enabled
```
Check again (after reboot later)
```
[ec2-user@ip-172-31-1-36 ~]$ cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]
```

#### Service nscd

Service nscd is not installed

```
yum install -y nscd
```

Enable on startup
```
chkconfig nscd on
```

Start
```
service nscd start
```

### Service ntpd

Service ntpd is not enabled on start
```
chkconfig ntpd on
```
Start
```
service ntpd start
```

### Reboot to make sure everything is set up fine








