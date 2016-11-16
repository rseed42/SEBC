## Cluster deployment


```
{
  "timestamp" : "2016-11-16T14:26:32.929Z",
  "clusters" : [ {
    "name" : "rseed42",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "2360344576"
          }, {
            "name" : "hive_metastore_server_max_message_size",
            "value" : "236034457"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "2360344576"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "912680550"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "153"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-23-134.ec2.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "c1oud3ra"
        }, {
          "name" : "hive_metastore_database_user",
          "value" : "cloudera"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-142b8c3f6a46910e93fab007596a28e9",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0e80905d19461dea4"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-1cef36e976d93626ae2b97382c54900d",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0b891d7bfc204bb61"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-778aea9b299916a1ddf50ff253aa4f16",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-07a00fbb2a9afcea6"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-bc943710dc01f4e51ee393a14b7625f9",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-082a35daf8b14a990"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-f9053ee6ca4d8d808d3300fa14fa9f79",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0bbe51ee83612e4ef"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-f9053ee6ca4d8d808d3300fa14fa9f79",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "i-0bbe51ee83612e4ef"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "57i339goeemj2ssag6smh5nfj"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-f9053ee6ca4d8d808d3300fa14fa9f79",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "i-0bbe51ee83612e4ef"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "aj739oyxfqxl8fb8rc6zbi4ki"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "694157312"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-142b8c3f6a46910e93fab007596a28e9",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-0e80905d19461dea4"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e6igpiyo9tkd3n8xd8epn55ce"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-1cef36e976d93626ae2b97382c54900d",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-0b891d7bfc204bb61"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3rluzjeu44g6tosi7sxwkn5bf"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-bc943710dc01f4e51ee393a14b7625f9",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-082a35daf8b14a990"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2mryov0bx1kc6mvwmnko6nfmq"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-172-31-23-134.ec2.internal"
        }, {
          "name" : "database_password",
          "value" : "c1oud3ra"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "database_user",
          "value" : "cloudera"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-f9053ee6ca4d8d808d3300fa14fa9f79"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-f9053ee6ca4d8d808d3300fa14fa9f79",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "i-0bbe51ee83612e4ef"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "b3b7zu4969d11sqykkuqittuo"
          }, {
            "name" : "secret_key",
            "value" : "Q4ILWAFvnMFB1e8HuelcyIJGUx4mIA"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-23-134.ec2.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-f9053ee6ca4d8d808d3300fa14fa9f79",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "i-0bbe51ee83612e4ef"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9q48hhkitou91960jd0ywahgl"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "2"
          } ]
        }, {
          "roleType" : "JOBHISTORY",
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "694157312"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "4078"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "resource_manager_java_heapsize",
            "value" : "694157312"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4078"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "Wc1cTn4eodqbqHhacwds2COUhpVxr5"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-bc943710dc01f4e51ee393a14b7625f9",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "i-082a35daf8b14a990"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6as7obblc2qsu7p60ji9rekjv"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-142b8c3f6a46910e93fab007596a28e9",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-0e80905d19461dea4"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dnaofwj4n8rnqllmeol6lbhsn"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-1cef36e976d93626ae2b97382c54900d",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-0b891d7bfc204bb61"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bn9nx89gaktdm2caz01z1owxw"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-778aea9b299916a1ddf50ff253aa4f16",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-07a00fbb2a9afcea6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4rr1z5sr8yl7wbzp9xuk97ew3"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-bc943710dc01f4e51ee393a14b7625f9",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-082a35daf8b14a990"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "f44qrbwacpo3yg7nyegx7wbh5"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-bc943710dc01f4e51ee393a14b7625f9",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "i-082a35daf8b14a990"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "115"
          }, {
            "name" : "role_jceks_password",
            "value" : "9pziyb7i4288q51m3r9s19qzl"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "694157312"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn03"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "5T38hNudo2roIKc9DY5wY9gbuvdgAZ"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "wh6B7UNJ36SD5MMxALaV4gXKcE5DmV"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "FwXnj6UNOVuJywA3v7zcFWTxGvFqT8"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-bc943710dc01f4e51ee393a14b7625f9",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "i-082a35daf8b14a990"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-142b8c3f6a46910e93fab007596a28e9",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-0e80905d19461dea4"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "eu7h1ezay7wszzpieziu7e6w8"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-1cef36e976d93626ae2b97382c54900d",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-0b891d7bfc204bb61"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "584bzwirxxhfko7qxw2so4zbg"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-778aea9b299916a1ddf50ff253aa4f16",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-07a00fbb2a9afcea6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4jdtyz0kmee2jctuprlycqoht"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-bc943710dc01f4e51ee393a14b7625f9",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-082a35daf8b14a990"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3qmbyu1c456qdqjfxvcjhh1tj"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-778aea9b299916a1ddf50ff253aa4f16",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-07a00fbb2a9afcea6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "82xjm5xikdzri4k4e12fbazbc"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-f9053ee6ca4d8d808d3300fa14fa9f79",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-0bbe51ee83612e4ef"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3gc9a0zdwjeg1wor6h74cnbyx"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-142b8c3f6a46910e93fab007596a28e9",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-0e80905d19461dea4"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn01"
          }, {
            "name" : "role_jceks_password",
            "value" : "ffyt9u18ut4xhv7lmnwnwj0z"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-778aea9b299916a1ddf50ff253aa4f16",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-07a00fbb2a9afcea6"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn03"
          }, {
            "name" : "role_jceks_password",
            "value" : "7hqz555h9prf4xxuh2iiiyuv9"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-f9053ee6ca4d8d808d3300fa14fa9f79",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-0bbe51ee83612e4ef"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn02"
          }, {
            "name" : "role_jceks_password",
            "value" : "8a6gl8cfgd0rhylh1wbclojr2"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-778aea9b299916a1ddf50ff253aa4f16",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-07a00fbb2a9afcea6"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "124"
          }, {
            "name" : "role_jceks_password",
            "value" : "3x4dg4jiazljdqw15iwfq8ewe"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-f9053ee6ca4d8d808d3300fa14fa9f79",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-0bbe51ee83612e4ef"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "118"
          }, {
            "name" : "role_jceks_password",
            "value" : "3q75zv0c1z4t7vk1c08mb4u17"
          } ]
        }
      }, {
        "name" : "hdfs-NFSGATEWAY-778aea9b299916a1ddf50ff253aa4f16",
        "type" : "NFSGATEWAY",
        "hostRef" : {
          "hostId" : "i-07a00fbb2a9afcea6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4xsmldgs0saefqgp0mfa21a61"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "i-082a35daf8b14a990",
    "ipAddress" : "172.31.18.1",
    "hostname" : "ip-172-31-18-1.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-0e80905d19461dea4",
    "ipAddress" : "172.31.22.145",
    "hostname" : "ip-172-31-22-145.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-0bbe51ee83612e4ef",
    "ipAddress" : "172.31.23.134",
    "hostname" : "ip-172-31-23-134.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-07a00fbb2a9afcea6",
    "ipAddress" : "172.31.25.204",
    "hostname" : "ip-172-31-25-204.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-0b891d7bfc204bb61",
    "ipAddress" : "172.31.28.101",
    "hostname" : "ip-172-31-28-101.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-bc943710dc01f4e51ee393a14b7625f9",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "6f02a71e12c1e676adc5858c4f26259f2cfc4b5c2ae18a771ad34e7f9d5da8f0",
    "pwSalt" : 7130339612067150958,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-bc943710dc01f4e51ee393a14b7625f9",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "509598b52b1f672ae12b3cbe72820504080e69414c4a978d2a4d3e17d66edb3e",
    "pwSalt" : -1896375696297857589,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-f9053ee6ca4d8d808d3300fa14fa9f79",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "9f920b49204ba6800b06dcdc98ef74c4d0fe5228d6d0876e760164e596289b95",
    "pwSalt" : -8129182235604399565,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-bc943710dc01f4e51ee393a14b7625f9",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "052c88fcafca12fe62a6adb435c734a13632a4c4dcfdc399c8b40b14f60f0f41",
    "pwSalt" : 4836694626889082448,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "231dc4ddae1fc82e3024858df80d7d1491f54caa668a72c575ca3897353b7c3f",
    "pwSalt" : -9169628468863653344,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "613cf11171fb41e81740a1261483afd4a462cdec3cdf2eb37ef0aa18691a7358",
    "pwSalt" : 5161028320631613317,
    "pwLogin" : true
  }, {
    "name" : "rseed42",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "fbe6974700f85511442282c9efeccd90f527e0f7b745c5af6b030f39db991fdb",
    "pwSalt" : 5716687295700432819,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.9.0",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20161006-1801",
    "gitHash" : "898a5e032c080e18833dfc58180761f6ef2ea351",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "694157312"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-23-134.ec2.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "c1oud3ra"
        }, {
          "name" : "headlamp_database_user",
          "value" : "cloudera"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-bc943710dc01f4e51ee393a14b7625f9",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "i-082a35daf8b14a990"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "av8s6w8rdqxxr3nzgm7tderze"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-bc943710dc01f4e51ee393a14b7625f9",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "i-082a35daf8b14a990"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "6s5ova7y7u6fbhflrk64sjbx1"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-bc943710dc01f4e51ee393a14b7625f9",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "i-082a35daf8b14a990"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "61iglktkds0stkdt0utbpp2e4"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-f9053ee6ca4d8d808d3300fa14fa9f79",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "i-0bbe51ee83612e4ef"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "atmmx27gffg7fvem8anhh9qvu"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-bc943710dc01f4e51ee393a14b7625f9",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "i-082a35daf8b14a990"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "4imtz1oe14cj1r7uiw3bcacdl"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/22/2012 13:40"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}
```