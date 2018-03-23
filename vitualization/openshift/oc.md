
# Openshift Client
## Installing openshift client in Windows
* Download the archive for your operating system from the [oc releases page](https://github.com/openshift/origin/releases/latest) and unpack it.
* Copy the contents of the directory to your preferred location.
* Add the oc binary to your PATH environment variable.

## OC Reference
* https://docs.openshift.com/enterprise/3.2/cli_reference/get_started_cli.html
* oc config view
* login
```
Set HOMEDRIVE=C:\Users\xxxx
oc login -u system:admin
```
# Openshift Type
```
oc types
```
* Nodes [node]: Machines set up in the cluster to run containers. Usually managed by administrators and not by end users.
* Projects [project]
* Containers: A definition of how to run one or more processes inside of a portable Linux environment.
* Image: A layered Linux filesystem that contains application code, dependencies, and any supporting operating system libraries. 
* Image Streams and Image Stream Tags [is,istag]:An image stream groups sets of related images under tags - analogous to a branch in a source code repository.
---
* Pods [pod]: A set of one or more containers that are deployed onto a Node together and share a unique IP and Volumes (persistent storage). Pods also define the security and runtime policy for each container.
* Services [svc]: A name representing a set of pods (or external servers) that are accessed by other pods. 
* Routes [route]: A route is an external DNS entry (either a top level domain or a dynamically allocated name) that is created to point to a service so that it can be accessed outside the cluster. 
---
* Volumes: Containers are not persistent by default - on restart their contents are cleared. Volumes are mounted filesystems available to Pods and their containers which may be backed by a number of host-local or network attached storage endpoints. 
* Secrets [secret]: The secret resource can hold text or binary secrets for delivery into your pods. 
* Labels: Labels are key value pairs that can be assigned to any resource in the system for grouping and selection.
---
* Builds [build]: Builds create a new image from source code, other images, Dockerfiles, or binary input. 
* Deployment Configuration [dc]: Defines the template for a pod and manages deploying new images or configuration changes whenever those change. 
* Replication Controllers [rc]: A replication controller maintains a specific number of pods based on a template that match a set of labels. 

Object Type | Abbreviated Version
--- | ---
build
`buildConfig` | bc
`deploymentConfig` | dc
event | ev
imageStream | is
imageStreamTag | istag
imageStreamImage | isimage
job
LimitRange | limits
node
`pod` | po
ResourceQuota | quota
`replicationController` | rc
`secrets`
`service` | svc
ServiceAccount | serviceaccounts
persistentVolume | pv
`persistentVolumeClaim` | pvc
# OC Basic Operation
https://docs.openshift.com/enterprise/3.2/cli_reference/basic_cli_operations.html
```
oc <action> <object_type> <object_name>
```
Action: get, describe, edit, delete, expose, create, update, export...


