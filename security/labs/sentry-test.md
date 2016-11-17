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

### Show (No) Tables


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

