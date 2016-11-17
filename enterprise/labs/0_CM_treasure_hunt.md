### What is ubertask optimization?

Can be enabled with option

```
mapreduce.job.ubertask.enable
```

Ubertask optimization runs "sufficiently small" jobs sequentially within a single JVM.

"Small" is defined by the:
```
mapreduce.job.ubertask.maxmaps
mapreduce.job.ubertask.maxreduces
mapreduce.job.ubertask.maxbytes 
```
settings

### Where in CM is the Kerberos Security Realm value displayed?

Administration -> Settings -> Kerberos -> Kerberos Security Realm

### Which CDH service(s) host a property for enabling Kerberos authentication?

Zookeeper has an "Enable Kerberos Authentication" property.


### How do you upgrade the CM agents?

1. Upgrade with Cloudera Manager (during CM upgrade).
2. Manually, by using the corresponding Linux package manager and restarting cloudera-scm-agent.

### Give the tsquery statement used to chart Hue's CPU utilization?

```
select cpu_system_rate + cpu_user_rate where category=ROLE and serviceName="Hue"
```

### Name all the roles that make up the Hive service

* Hive Gateway
* Hive Metastore Server
* HiveServer2

### What steps must be completed before integrating Cloudera Manager with Kerberos?

The Cloudera manager account "cloudera-scm" must be configured in the Kerberos kadm5.acl file.
