# Installation
## Windows
https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/
* Download MongoDB from https://www.mongodb.org/dl/win32/x86_64-2008plus-ssl 
* Install msi(Run as Administrator) or unzip from zip file on C:\Program Files\MongoDB\Server\3.6
* Create MongoDB data and log folder
* Create a configuration file C:\Program Files\MongoDB\Server\3.6\mongod.cfg.

```
systemLog:
  destination: "file"
  path: "c:\\data\\log\\mongod.log"
storage:
  dbPath: "c:\\data\\db
```

* Install and start the MongoDB service(Run as Administrator)

```
"C:\Program Files\MongoDB\Server\3.6\bin\mongod.exe" ^
  --config "C:\Program Files\MongoDB\Server\3.6\mongod.cfg" ^
  --install
```

# Security
## Enable authentication 
https://docs.mongodb.com/master/tutorial/enable-authentication/
* Create admin user (use mongo

```
use admin
db.createUser(
  {
    user: "admin",
    pwd: "password",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
  }
)
```

* Re-start the mongod instance with the --auth command line option or, if using a onfiguration file, the security.authorization setting.

```
security:
  authorization: enabled
setParameter:
   enableLocalhostAuthBypass: false
```
# Performance
## Performance problem
* Incorrect indexes(too few or too many)

## Profiling
### Enable profiling
https://docs.mongodb.com/manual/tutorial/manage-the-database-profiler/


# Reference
* [MongoDB – quick and secure installation with authorization](https://www.youtube.com/watch?v=gg6r4-xaTyI)
* [MongoDB config options](https://docs.mongodb.com/master/reference/configuration-options)
