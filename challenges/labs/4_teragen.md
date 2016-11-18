## Teragen


### Run teragen

```
time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen \
-Dmapreduce.job.maps=8 \
-Ddfs.block.size=16777216 \
51200000 \
/user/bavaria/tgen512m
```


### Check generated data

```
[bavaria@ip-172-31-1-36 root]$ hdfs dfs -ls /user/bavaria/tgen512m
Found 9 items
-rw-r--r--   3 bavaria bavaria          0 2016-11-18 05:57 /user/bavaria/tgen512m/_SUCCESS
-rw-r--r--   3 bavaria bavaria  640000000 2016-11-18 05:57 /user/bavaria/tgen512m/part-m-00000
-rw-r--r--   3 bavaria bavaria  640000000 2016-11-18 05:57 /user/bavaria/tgen512m/part-m-00001
-rw-r--r--   3 bavaria bavaria  640000000 2016-11-18 05:52 /user/bavaria/tgen512m/part-m-00002
-rw-r--r--   3 bavaria bavaria  640000000 2016-11-18 05:57 /user/bavaria/tgen512m/part-m-00003
-rw-r--r--   3 bavaria bavaria  640000000 2016-11-18 05:57 /user/bavaria/tgen512m/part-m-00004
-rw-r--r--   3 bavaria bavaria  640000000 2016-11-18 05:55 /user/bavaria/tgen512m/part-m-00005
-rw-r--r--   3 bavaria bavaria  640000000 2016-11-18 05:57 /user/bavaria/tgen512m/part-m-00006
-rw-r--r--   3 bavaria bavaria  640000000 2016-11-18 05:57 /user/bavaria/tgen512m/part-m-00007
```

### Check the number of blocks

```
[bavaria@ip-172-31-1-36 root]$ hdfs fsck /user/bavaria/tgen512m -blocks
Connecting to namenode via http://ip-172-31-1-32.ec2.internal:50070
FSCK started by bavaria (auth:SIMPLE) from /172.31.1.36 for path /user/bavaria/tgen512m at Fri Nov 18 05:58:45 EST 2016
.........Status: HEALTHY
 Total size:    5120000000 B
 Total dirs:    1
 Total files:   9
 Total symlinks:                0
 Total blocks (validated):      312 (avg. block size 16410256 B)
 Minimally replicated blocks:   312 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Fri Nov 18 05:58:45 EST 2016 in 16 milliseconds


The filesystem under path '/user/bavaria/tgen512m' is HEALTHY
```
