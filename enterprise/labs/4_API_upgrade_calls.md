## API Upgrade Calls

Check latest supported version

```
curl -u admin:admin 'http://localhost:7180/api/version'
```

```
v14
```

-> The latest supported api version is v14


Check the version of Cloudera Manager

```
curl -u admin:admin 'http://localhost:7180/api/v1/cm/version'
```

```
{
  "version" : "5.9.0",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20161006-1801",
  "gitHash" : "898a5e032c080e18833dfc58180761f6ef2ea351",
  "snapshot" : false
}
```

CM is version 5.9.0

```
curl -u admin:admin 'http://localhost:7180/api/v1/users'
```

```
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  }, {
    "name" : "rseed42",
    "roles" : [ "ROLE_LIMITED" ]
  } ]
}
```

Users:

* admin
* minotaur
* rseed42


Database used by Cloudera Manager.

This is not available in v1, so we need to use a later API version:

```
curl -u admin:admin 'http://localhost:7180/api/v14/cm/scmDbInfo'
```

```
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```
