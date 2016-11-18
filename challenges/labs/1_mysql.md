## MySQL Setup

### MySQL Installation

```
wget http://dev.mysql.com/get/mysql57-community-release-el6-9.noarch.rpm
rpm -ivh mysql57-community-release-el6-9.noarch.rpm
```

Enabled version 5.6 in /etc/yum.repos.d/mysql-community.repo

```
yum update
```
Install MySQL

```
yum install mysql-server
```
Check version

```
[root@ip-172-31-1-36 ~]# mysqld --version
mysqld  Ver 5.6.34 for Linux on x86_64 (MySQL Community Server (GPL))
```

Service mysqld is enabled for runlevels 345 automatically after install
```
[root@ip-172-31-1-36 ~]# chkconfig --list mysqld
mysqld          0:off   1:off   2:off   3:on    4:on    5:on    6:off
```

Start
```
service mysqld start
```

Installed mysql client on all nodes (older client version on the clients shouldn't be a problem)

```
yum install -y mysql
```

### JDBC driver

Download tarball

```
wget http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.40.tar.gz
tar -xzf mysql-connector-java-5.1.40.tar.gz
```
Decompress and copy the driver to a system directory.
Make sure it is called mysql-connector-java.jar!

```
mkdir -p /usr/share/java/
cp mysql-connector-java-5.1.40/mysql-connector-java-5.1.40-bin.jar /usr/share/java/mysql-connector-java.jar
```



