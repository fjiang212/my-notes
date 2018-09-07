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
* Create admin user (use mongo shell)

```
use admin
db.createUser(
  {
    user: "admin",
    pwd: "password",
    roles: [ { role: "root", db: "admin" } ]
  }
)
```

* Re-start the mongod instance with the --auth command line option or, if using a configuration file, the security.authorization setting.

```
security:
  authorization: enabled
setParameter:
   enableLocalhostAuthBypass: false
```

* Login with admin 

```
C:\Program Files\MongoDB\Server\4.0\bin>mongo localhost/clientapp -u admin -p password --authenticationDatabase admin
```

* Create new database and user
```
> use client
switched to db client
> db.createUser(
...   {
...     user: "client",
...     pwd: "password",
...     roles: [ { role: "dbOwner", db: "client" } ]
...   }
... )
```

## Roles
https://docs.mongodb.com/manual/reference/built-in-roles/#database-user-roles


# Data Management
## Import data
* From commandline

```
C:\Program Files\MongoDB\Server\4.0\bin>mongoimport /username:client /password:password /authenticationDatabase:client --db client --collection zips --file C:\tmp\zips.json
```

* From shell or UI tool to insert documents 

# Commands
## 
|Help Methods and Commands |   Description|
| :--- | :--------------------------  |
|help  |  Show help.|
|db.help() |  Show help for database methods.|
|db.<collection>.help() | Show help on collection methods. The <collection> can be the name of an existing collection or a non-existing collection.|
|show dbs |   Print a list of all databases on the server.|
|use <db>  |  Switch current database to <db>. The mongo shell variable db is set to the current database.|
|show collections | Print a list of all collections for current database.|
|show users | Print a list of users for current database.|
|show roles | Print a list of all roles, both user-defined and built-in, for the current database.|
|show profile |   Print the five most recent operations that took 1 millisecond or more. See documentation on the database profiler for more information.|
|show databases | Print a list of all available databases.|
|load()  |Execute a JavaScript file. See Write Scripts for the mongo Shell for more information.|
# Performance
## Performance problem
* Incorrect indexes(too few or too many)

## Profiling
### Enable profiling
https://docs.mongodb.com/manual/tutorial/manage-the-database-profiler/


# Reference
* [MongoDB – quick and secure installation with authorization](https://www.youtube.com/watch?v=gg6r4-xaTyI)
* [MongoDB config options](https://docs.mongodb.com/master/reference/configuration-options)
