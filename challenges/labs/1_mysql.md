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

### JDBC Driver

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


### Database Setup

* Set up a new root password
* Removed table test


Set up databases

```
scm
rman
hive
oozie
hue
sentry
```

Create databases
```
create database scm DEFAULT CHARACTER SET utf8;
create database rman DEFAULT CHARACTER SET utf8;
create database hive DEFAULT CHARACTER SET utf8;
create database oozie DEFAULT CHARACTER SET utf8;
create database hue DEFAULT CHARACTER SET utf8;
create database sentry DEFAULT CHARACTER SET utf8;
```

Grant privileges
```
grant all on scm.* TO 'scm'@'%' IDENTIFIED BY 'scm';
grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman';
grant all on hive.* TO 'hive'@'%' IDENTIFIED BY 'hive';
grant all on oozie.* TO 'oozie'@'%' IDENTIFIED BY 'oozie';
grant all on hue.* TO 'hue'@'%' IDENTIFIED BY 'hue';
grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'sentry';
```

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)
```

```
mysql> show grants for 'scm';
+----------------------------------------------------------------------------------------------------+
| Grants for scm@%                                                                                   |
+----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'scm'@'%' IDENTIFIED BY PASSWORD '*45E6E3C68BDF1AC7EBB5C5A3BCBD5E9437B293BE' |
| GRANT ALL PRIVILEGES ON `scm`.* TO 'scm'@'%'                                                       |
| GRANT ALL PRIVILEGES ON `sentry`.* TO 'scm'@'%'                                                    |
| GRANT ALL PRIVILEGES ON `hue`.* TO 'scm'@'%'                                                       |
+----------------------------------------------------------------------------------------------------+
4 rows in set (0.01 sec)

mysql> show grants for 'rman';
+-----------------------------------------------------------------------------------------------------+
| Grants for rman@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'rman'@'%' IDENTIFIED BY PASSWORD '*819397F8B454D58DA4E9F42A88A4873756B8C96D' |
| GRANT ALL PRIVILEGES ON `rman`.* TO 'rman'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> show grants for 'hive';
+-----------------------------------------------------------------------------------------------------+
| Grants for hive@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'hive'@'%' IDENTIFIED BY PASSWORD '*4DF1D66463C18D44E3B001A8FB1BBFBEA13E27FC' |
| GRANT ALL PRIVILEGES ON `hive`.* TO 'hive'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> show grants for 'oozie';
+------------------------------------------------------------------------------------------------------+
| Grants for oozie@%                                                                                   |
+------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'oozie'@'%' IDENTIFIED BY PASSWORD '*2B03FE0359FAD3B80620490CE614F8622E0828CD' |
| GRANT ALL PRIVILEGES ON `oozie`.* TO 'oozie'@'%'                                                     |
+------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> show grants for 'hue';
+----------------------------------------------------------------------------------------------------+
| Grants for hue@%                                                                                   |
+----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'hue'@'%' IDENTIFIED BY PASSWORD '*15221DE9A04689C4D312DEAC3B87DDF542AF439E' |
| GRANT ALL PRIVILEGES ON `hue`.* TO 'hue'@'%'                                                       |
+----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> show grants for 'sentry';
+-------------------------------------------------------------------------------------------------------+
| Grants for sentry@%                                                                                   |
+-------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'sentry'@'%' IDENTIFIED BY PASSWORD '*78CD2A8CB7403E99F97588EDF05B3EEAC6494302' |
| GRANT ALL PRIVILEGES ON `sentry`.* TO 'sentry'@'%'                                                    |
+-------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

```


