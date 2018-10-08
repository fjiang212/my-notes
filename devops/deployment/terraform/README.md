# What is Terraform
Terraform is a tool for building, changing, and versioning infrastructure safely and efficiently. Terraform can manage existing and popular service providers as well as custom in-house solutions.

The key features of Terraform are:
* Infrastructure as Code
* Execution Plans
* Resource Graph
* Change Automation

# Key Concepts
* **Provider**: Providers are responsible in Terraform for managing the lifecycle of a resource: create, read, update, delete.
* **Module**: Modules in Terraform are self-contained packages of Terraform configurations that are managed as a group. Modules are used to create reusable components, improve organization, and to treat pieces of infrastructure as a black box.
* **Resource**: Resources are a component of your infrastructure.
* **Data Source**: Data sources allow data to be fetched or computed for use elsewhere in Terraform configuration.
* **Provisioners**: Provisioners are used to execute scripts on a local or remote machine as part of resource creation or destruction. 
* **Workspace**: Each Terraform configuration has an associated backend that defines how operations are executed and where persistent data such as the Terraform state are stored.The persistent data stored in the backend belongs to a workspace
* **Remote Backends**: Remote backends allow Terraform to use a shared storage space for state data, so any member of your team can use Terraform to manage the same infrastructure.
* **interpolation expression**:  Embedded within strings in Terraform, whether you're using the Terraform syntax or JSON syntax, you can interpolate other values


# Commands

```
Common commands:
    apply              Builds or changes infrastructure
    console            Interactive console for Terraform interpolations
    destroy            Destroy Terraform-managed infrastructure
    env                Workspace management
    fmt                Rewrites config files to canonical format
    get                Download and install modules for the configuration
    graph              Create a visual graph of Terraform resources
    import             Import existing infrastructure into Terraform
    init               Initialize a Terraform working directory
    output             Read an output from a state file
    plan               Generate and show an execution plan
    providers          Prints a tree of the providers used in the configuration
    push               Upload this Terraform module to Atlas to run
    refresh            Update local state file against real resources
    show               Inspect Terraform state or plan
    taint              Manually mark a resource for recreation
    untaint            Manually unmark a resource as tainted
    validate           Validates the Terraform files
    version            Prints the Terraform version
    workspace          Workspace management

All other commands:
    debug              Debug output management (experimental)
    force-unlock       Manually unlock the terraform state
    state              Advanced state management
```

## Q & A
* Q1. Failed Provisioners and Tainted Resources

If a resource successfully creates but fails during provisioning, Terraform will error and mark the resource as **"tainted"**. A resource that is tainted has been physically created, but can't be considered safe to use since provisioning failed.
When you generate your next execution plan,Terraform will remove any tainted resources and create new resources, attempting to provision them again after creation.

* Q2. Where is variable value coming from
  * Variable has to be defined in each module variables.tf
  * Module can create output variable in output.tf
  * Variable value can be read from root variable (${var.xxx}) or other module output (${module.modulea.xxx})
  
# Coding
* https://www.terraform.io/docs/index.html
* https://www.terraform.io/docs/configuration/index.html

## Module 
* Inputs of a module are variables and outputs are outputs.
* Module structure
```
$ tree complete-module/
.
├── README.md
├── main.tf
├── variables.tf
├── outputs.tf
├── ...
├── modules/
│   ├── nestedA/
│   │   ├── README.md
│   │   ├── variables.tf
│   │   ├── main.tf
│   │   ├── outputs.tf
│   ├── nestedB/
│   ├── .../
├── examples/
│   ├── exampleA/
│   │   ├── main.tf
│   ├── exampleB/
│   ├── .../
```


## Variable 
https://www.terraform.io/intro/getting-started/variables.html

### Assigning Variables
* Command-line flags
```
$ terraform apply \
  -var 'access_key=foo' \
  -var 'secret_key=bar'
```

* From a file
```
$ terraform apply \
  -var-file="secret.tfvars" \
  -var-file="production.tfvars"
```
For all files which match **terraform.tfvars** or *.auto.tfvars present in the current directory, Terraform automatically loads them to populate variables.

* From environment variables: **TF_VAR_name**
* UI Input
* Variable Defaults

### Variable Reference
* User string variables
```
${var.foo}
```
* User map variables
```
${var.amis["us-east-1"]}
```
* User list variables
```
${var.subnets}
${var.subnets[idx]}
```
* Attributes of your own resource
```
${self.private_ip}
```
* Attributes of other resources
```
${aws_instance.web.id}

// access individual attributes with a zero-based index, such as 
${aws_instance.web.0.id}

// use the splat syntax to get a list of all the attributes: 
${aws_instance.web.*.id}.
```
* Attributes of a data source
```
${data.aws_ami.ubuntu.id} 
```
* Outputs from a module
```
The syntax is MODULE.NAME.OUTPUT. For example ${module.foo.bar} 
```
* Count information
```
${count.index} will interpolate the current index in a multi-count resource
```
* Path information
```
The syntax is path.TYPE. TYPE can be cwd, module, or root.
```
* Terraform meta information
```
The syntax is terraform.FIELD. This variable type contains metadata about the currently executing Terraform run. 
```
## Functions
https://www.terraform.io/docs/configuration/interpolation.html#built-in-functions


## Template
https://www.terraform.io/docs/configuration/interpolation.html#templates

# References
* https://www.terraform.io/intro/index.html
* https://github.com/linuxacademy/content-terraform  
