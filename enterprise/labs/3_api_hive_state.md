## Start and Stop Hive via the CM REST API

First, let's abbreviate the URL:

```
URL=http://localhost:7180/api/v1
```

Stop Hive

```
curl -X POST -u admin:admin "$URL/clusters/rseed42/services/hive/commands/stop"
```

```
{
  "id" : 596,
  "name" : "Stop",
  "startTime" : "2016-11-16T15:16:31.006Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

The command id is returned in the JSON output. Using it,
we can check the status of the command:

```
curl -u admin:admin "$URL/commands/596"
```


```
{
  "id" : 596,
  "name" : "Stop",
  "startTime" : "2016-11-16T15:16:31.006Z",
  "endTime" : "2016-11-16T15:16:44.228Z",
  "active" : false,
  "success" : true,
  "resultMessage" : "Successfully stopped service.",
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  },
```

Start Hive
```
curl -X POST -u admin:admin "$URL/clusters/rseed42/services/hive/commands/start"
```

```
{
  "id" : 600,
  "name" : "Start",
  "startTime" : "2016-11-16T15:19:14.450Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```


Check again

```
curl -u admin:admin "$URL/commands/600"
````

```
{
  "id" : 600,
  "name" : "Start",
  "startTime" : "2016-11-16T15:19:14.450Z",
  "endTime" : "2016-11-16T15:19:36.752Z",
  "active" : false,
  "success" : true,
  "resultMessage" : "Successfully started service.",
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  },
```


