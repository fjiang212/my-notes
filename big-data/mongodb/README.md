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


# Reference
* [MongoDB – quick and secure installation with authorization](https://www.youtube.com/watch?v=gg6r4-xaTyI)
