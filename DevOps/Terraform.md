```
⭐️ Arise, awake, and stop not till the goal is reached.
– Swami Vivekananda

⭐️ You don’t learn to walk by following rules. You learn by doing, and falling over.
– Richard Branson

⭐️ The things always happens that you really believe in; and the belief in a thing makes it happen.
– Frank Lloyd Wright

⭐️ The most important thing to do in solving a problem is to begin.
– Frank Tyger
```
# Objectives
- Introduction to IaC
- Types of IaC
- Why Terraform?
- HCL Basics
- Provision Update & Destroy
- Providers
- Input Variables
- Output Variables
- Resource Attribution
- Resource Dependencies
---
# Traditional Infra Provision Challenge
- Big turnaround time from request to provision
- Unavailability of auto scaling
- Underutilising the resource
---
### Infrastructure as Code (IaC)
- We can go to aws console and create a resource
- But rather than doing this every time, we can write a code & it can be something as simple as shell script which can do it, is called Infrastructure as code
- Some Common Tools
	- ### Provisioning Tools (The ones which provides underlying infra)
		- Terraform
		- CloudFormation
	- ### Configuration Management (The ones which configure infra once provisioned by earlier category)
		- Ansible
		- Puppet
		- SaltStack
	- ### Server Templating
		- Docker
		- Packer
		- Vagrant
---
# Why Terraform?
- Free & Open Source
- Installs as single binary
- Ability to deploy on multiple platforms like aws, google cloud, azure, vsphere, github etc
- This is achieved by providers
	- Providers help manage third party platforms using their APIs
- It uses HCL (Hashicorp Configuration Language)
```HCL
resource "aws_iam_user" "admin-user" {
	name = "lucy"
		tags = {
		Description = "Team Leader"
	}
}  
```
- init --> plan --> apply
	- init - Identifies & downloads the providers to be used
	- plan - Drafts plan for infra creation
	- apply - creates infra
- ![](attachments/Screenshot%202025-12-01%20at%2010.16.39%20AM.png)
- Terraform Can bring already created infrastructure under it's umbrella so it can be managed later
---
# Some Common Namings in terraform
- Configuration File - Any file like main.tf which has configuration required to create a resource
- Resource - Anything which can be created using configuration file, like a s3 bucket, azure vm or something as simple as file
- .tfstate - It's basically a blueprint for terraform. It checks what is the current state of resources from terraform and apply Configuration file on it
- HCL - Hashicorp Configuration Language
---
# HCL
- ## Syntax
```HCL
<block> <parameters> {
	key1 = value1
	key2 = value2
}
```

```HCL
resource "local_file" "pet" {
	filename = "/root/pet.txt"
	content = "We Love Pets!"
}
```

Here,
- Block = `resource`, there are also other type of blocks like - data, variable, output etc
- ![](attachments/Screenshot%202025-12-01%20at%2010.34.51%20AM.png)
- Think this like a function
```
def sum {
sum = a + b
}
```
- `resource` is like def but there can be multiple other types than just def, so like data, variable, output etc
- 'local_file' - it's like name of function but it can't be changed and it's system default. It's different for different different providers.
	- But all providers following rule that first word is going to be provider and 2nd type of resource
- `pet` - it's like name of block for us to understand & use later in code
- `filename & content` = are like a & b, they are specific to resource type and can't be changed, only their values can be changed
---
# Workflow
- Write terraform configuration file
```
resource "local_file" "pet" {
	filename = "/root/pet.txt"
	content = "We Love Pets!"
}
```
- Run `terraform init`
	- Will check configuration
	- Initialize the configuration, like download plugin and all
	- It actually creates file name `.terraform.lock.hcl` which contains info about what plugins downloaded
	- ![](attachments/Screenshot%202025-12-02%20at%209.35.51%20AM.png)
- Run `terraform plan`
	- It will show actions that will be carried out by terraform
	- ![](attachments/Screenshot%202025-12-02%20at%208.45.30%20AM.png)
	- you can save plan using `-out` flag
		- Will display execution plan once again
		- Will ask user to confirm and once confirmed will proceed ahead
- Run `terraform apply`
---
# Update & Destroy Infrastructure
- Terraform created immutable resource
	- That means, if you create local_file with permission 777 and now try to change it to 007, it will remove whole file and recreate it rather than just updating
- Use `terraform destroy` to destroy the infrastructure
---
# Providers
- Type Of Providers- ![](attachments/Screenshot%202025-12-02%20at%209.10.59%20AM.png)
	- Official - Maintained by terraform
	- Partner - Maintained by organization
	- Community - Separate organization or open source
---
# Some common output files
- main.tf - Main configurational file
- variable.tf - Contains variable declaration
- outputs.tf - Contains output from resources
- provider.tf - Contains provider definition
---
# Variables
- we can use `variables.tf`
```HCL
variable "filename" {
	default = "/root/abc.txt"
	type = string #Optional
	description = "Name of the file" #Optional
}

variable "content" {
	default = "Content Goes Here"
}
```
- And then we can use it in main.tf like below
```HCL
resource "local_file" "new-file" {
	filename = var.filename
	content = var.content
}
```
## Basic Variables Types which can be used are
- string, number, bool, any, list, map, object, tuple
- ## list
```var.tf
variable "prefix" {
	default = ["Mr", "Mrs", "Sir"]
	type = list
}
```

```main.tf
resource "local_file" "name.txt" {
	filename = /root/var.prefix[0]
	content = var.prefix[0]
}
```
- ## Map
```var.tf
variable "file-content" {
	type = map
	default = {
		"statement1" = "This is statement 1"
		"statement2" = "This is statement 2"
	}
}
```

```main.tf
resource "local_file" "file" {
	filename = abc.txt
	content = var.file-content["statement1"]
}
```

- ## Set
	- Similar like python, in set type of terraform variable, it don't allow duplicate value
- ## Object
  - ![](attachments/Screenshot%202025-12-02%20at%2011.14.26%20AM.png)
- ## Tuple
	- It's similar like list but allows multiple type of variables
```var.tf
variable kitty {
	type = tuple([string, number, bool])
	default = ["cat", 10, true]
}
```
---
# Common Questions
- How can I make Terraform apply run without asking for confirmation?
	- --> `terraform apply -auto-approve`
- 




