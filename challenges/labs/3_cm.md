### Install CDH

## Check Grants

```
mysql> show grants for rman;
+-----------------------------------------------------------------------------------------------------+
| Grants for rman@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'rman'@'%' IDENTIFIED BY PASSWORD '*819397F8B454D58DA4E9F42A88A4873756B8C96D' |
| GRANT ALL PRIVILEGES ON `rman`.* TO 'rman'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> show grants for hive;
+-----------------------------------------------------------------------------------------------------+
| Grants for hive@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'hive'@'%' IDENTIFIED BY PASSWORD '*4DF1D66463C18D44E3B001A8FB1BBFBEA13E27FC' |
| GRANT ALL PRIVILEGES ON `hive`.* TO 'hive'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> show grants for scm;
+----------------------------------------------------------------------------------------------------+
| Grants for scm@%                                                                                   |
+----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'scm'@'%' IDENTIFIED BY PASSWORD '*45E6E3C68BDF1AC7EBB5C5A3BCBD5E9437B293BE' |
+----------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

```

### Create HDFS User Directories

```
hdfs dfs -mkdir -p /user/bavaria
hdfs dfs -chown bavaria:bavaria /user/bavaria
hdfs dfs -mkdir -p /user/saxony
hdfs dfs -chown saxony:saxony /user/saxony
```

### HDFS Directories

```
[hdfs@ip-172-31-1-32 root]$ hdfs dfs -ls /user
Found 2 items
drwxr-xr-x   - bavaria bavaria          0 2016-11-18 05:45 /user/bavaria
drwxr-xr-x   - saxony  saxony           0 2016-11-18 05:45 /user/saxony
```

### Hosts API Call
```
[root@ip-172-31-1-35 ~]# curl -u admin:admin 'http://localhost:7180/api/v12/hosts'
{
  "items" : [ {
    "hostId" : "i-0521c6de03c6014a1",
    "ipAddress" : "172.31.1.32",
    "hostname" : "ip-172-31-1-32.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-1-35.ec2.internal:7180/cmf/hostRedirect/i-0521c6de03c6014a1",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664844800
  }, {
    "hostId" : "i-0cc35e9b4d2ab2ccc",
    "ipAddress" : "172.31.1.33",
    "hostname" : "ip-172-31-1-33.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-1-35.ec2.internal:7180/cmf/hostRedirect/i-0cc35e9b4d2ab2ccc",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664844800
  }, {
    "hostId" : "i-0c22c7e8fb010a0e0",
    "ipAddress" : "172.31.1.34",
    "hostname" : "ip-172-31-1-34.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-1-35.ec2.internal:7180/cmf/hostRedirect/i-0c22c7e8fb010a0e0",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664844800
  }, {
    "hostId" : "i-0f2e16628762dc6ac",
    "ipAddress" : "172.31.1.35",
    "hostname" : "ip-172-31-1-35.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-1-35.ec2.internal:7180/cmf/hostRedirect/i-0f2e16628762dc6ac",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664844800
  }, {
    "hostId" : "i-01f355d093aaa6d31",
    "ipAddress" : "172.31.1.36",
    "hostname" : "ip-172-31-1-36.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-1-35.ec2.internal:7180/cmf/hostRedirect/i-01f355d093aaa6d31",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664844800
  } ]
}
```