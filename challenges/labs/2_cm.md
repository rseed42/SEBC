## Cloudera Manager Installation

Install on Node 04
```
ip-172-31-1-35.ec2.internal
```

### CM Repo Setup

Add new yum repo

```
wget https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/cloudera-manager.repo
```

Change the version of Cloudera Manager in cloudera-manager.repo

```
#baseurl=https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5/
baseurl=https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5.7.4
```

Update yum

```
cp cloudera-manager.repo /etc/yum.repos.d/
yum update
```

```
yum repolist all
```


### Update MySQL Authorization for scm

```
REVOKE all ON scm.* FROM 'scm'@'%';
```

```
mysql> show grants for 'scm';
+----------------------------------------------------------------------------------------------------+
| Grants for scm@%                                                                                   |
+----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'scm'@'%' IDENTIFIED BY PASSWORD '*45E6E3C68BDF1AC7EBB5C5A3BCBD5E9437B293BE' |
+----------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
```

```
grant all on scm.* TO 'scm'@'ip-172-31-1-35.ec2.internal' IDENTIFIED BY 'scm';
```

```
mysql> show grants for 'scm'@'ip-172-31-1-35.ec2.internal';
+------------------------------------------------------------------------------------------------------------------------------+
| Grants for scm@ip-172-31-1-35.ec2.internal                                                                                   |
+------------------------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'scm'@'ip-172-31-1-35.ec2.internal' IDENTIFIED BY PASSWORD '*45E6E3C68BDF1AC7EBB5C5A3BCBD5E9437B293BE' |
| GRANT ALL PRIVILEGES ON `scm`.* TO 'scm'@'ip-172-31-1-35.ec2.internal'                                                       |
+------------------------------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)
```

### Install JDK

```
sudo yum install oracle-j2sdk1.7
```

### Install Cloudera Manager


```
sudo yum install cloudera-manager-daemons cloudera-manager-server
```


### Prepare database

```
/usr/share/cmf/schema/scm_prepare_database.sh -h ip-172-31-1-36.ec2.internal mysql scm scm scm
```

### Start Server

```
service cloudera-scm-server start
```