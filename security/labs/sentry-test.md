## Sentry Test

### Connection with Beeline


```
[rseed42@ip-172-31-25-204 root]$ beeline
2016-11-17 14:14:27,376 WARN  [main] mapreduce.TableMapReduceUtil: The hbase-prefix-tree module jar containing PrefixTreeCodec is not present.  Continuing without it.
Beeline version 1.1.0-cdh5.9.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-23-134.ec2.internal:10000/default;principal=hive/ip-172-31-23-134.ec2.internal@RSEED42.COM
scan complete in 1ms
Connecting to jdbc:hive2://ip-172-31-23-134.ec2.internal:10000/default;principal=hive/ip-172-31-23-134.ec2.internal@RSEED42.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.0)
Driver: Hive JDBC (version 1.1.0-cdh5.9.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-23-134.ec2.internal>
```

### Show (No) Tables (Initial Config)


```
0: jdbc:hive2://ip-172-31-23-134.ec2.internal> show tables;
INFO  : Compiling command(queryId=hive_20161117141717_c82ec267-ad4f-437e-87dd-ae8636039b2e): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20161117141717_c82ec267-ad4f-437e-87dd-ae8636039b2e); Time taken: 0.688 seconds
INFO  : Executing command(queryId=hive_20161117141717_c82ec267-ad4f-437e-87dd-ae8636039b2e): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117141717_c82ec267-ad4f-437e-87dd-ae8636039b2e); Time taken: 0.242 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.283 seconds)
```

### George's Session

```
[george@ip-172-31-18-1 root]$ kinit
Password for george@RSEED42.COM:
[george@ip-172-31-18-1 root]$ klist
Ticket cache: FILE:/tmp/krb5cc_1100
Default principal: george@RSEED42.COM

Valid starting       Expires              Service principal
11/17/2016 15:13:32  11/18/2016 15:13:32  krbtgt/RSEED42.COM@RSEED42.COM
        renew until 11/24/2016 15:13:32
```

```
[george@ip-172-31-18-1 root]$ beeline
2016-11-17 15:14:20,638 WARN  [main] mapreduce.TableMapReduceUtil: The hbase-prefix-tree module jar containing PrefixTreeCodec is not present.  Continuing without it.
Beeline version 1.1.0-cdh5.9.0 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-23-134.ec2.internal:10000/default;principal=hive/ip-172-31-23-134.ec2.internal@RSEED42.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-23-134.ec2.internal:10000/default;principal=hive/ip-172-31-23-134.ec2.internal@RSEED42.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.0)
Driver: Hive JDBC (version 1.1.0-cdh5.9.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
```


```
0: jdbc:hive2://ip-172-31-23-134.ec2.internal> use default;
INFO  : Compiling command(queryId=hive_20161117151414_957b70eb-3f8c-4fca-82bc-01c1518cddab): use default
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117151414_957b70eb-3f8c-4fca-82bc-01c1518cddab); Time taken: 0.125 seconds
INFO  : Executing command(queryId=hive_20161117151414_957b70eb-3f8c-4fca-82bc-01c1518cddab): use default
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117151414_957b70eb-3f8c-4fca-82bc-01c1518cddab); Time taken: 0.025 seconds
INFO  : OK
No rows affected (0.207 seconds)
0: jdbc:hive2://ip-172-31-23-134.ec2.internal> show tables;
INFO  : Compiling command(queryId=hive_20161117151414_8ffd00a0-c152-4c74-a2c2-deb85878213f): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20161117151414_8ffd00a0-c152-4c74-a2c2-deb85878213f); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20161117151414_8ffd00a0-c152-4c74-a2c2-deb85878213f): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117151414_8ffd00a0-c152-4c74-a2c2-deb85878213f); Time taken: 0.103 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
| test       |
+------------+--+
2 rows selected (0.213 seconds)
```


### George's Session

```
[ferdinand@ip-172-31-28-101 root]$ kinit
Password for ferdinand@RSEED42.COM:
[ferdinand@ip-172-31-28-101 root]$ klist
Ticket cache: FILE:/tmp/krb5cc_1200
Default principal: ferdinand@RSEED42.COM

Valid starting       Expires              Service principal
11/17/2016 15:15:58  11/18/2016 15:15:58  krbtgt/RSEED42.COM@RSEED42.COM
        renew until 11/24/2016 15:15:58
```

```
beeline> !connect jdbc:hive2://ip-172-31-23-134.ec2.internal:10000/default;principal=hive/ip-172-31-23-134.ec2.internal@RSEED42.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-23-134.ec2.internal:10000/default;principal=hive/ip-172-31-23-134.ec2.internal@RSEED42.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.0)
Driver: Hive JDBC (version 1.1.0-cdh5.9.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
```


```
0: jdbc:hive2://ip-172-31-23-134.ec2.internal> use default;
INFO  : Compiling command(queryId=hive_20161117151616_9c809bbc-d9d8-4197-851b-c9f2c481453b): use default
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117151616_9c809bbc-d9d8-4197-851b-c9f2c481453b); Time taken: 0.133 seconds
INFO  : Executing command(queryId=hive_20161117151616_9c809bbc-d9d8-4197-851b-c9f2c481453b): use default
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117151616_9c809bbc-d9d8-4197-851b-c9f2c481453b); Time taken: 0.024 seconds
INFO  : OK
No rows affected (0.215 seconds)
0: jdbc:hive2://ip-172-31-23-134.ec2.internal> show tables;
INFO  : Compiling command(queryId=hive_20161117151616_e34a11c9-4059-476f-9e98-918cfa66a780): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20161117151616_e34a11c9-4059-476f-9e98-918cfa66a780); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20161117151616_e34a11c9-4059-476f-9e98-918cfa66a780): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117151616_e34a11c9-4059-476f-9e98-918cfa66a780); Time taken: 0.109 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.216 seconds)
```



