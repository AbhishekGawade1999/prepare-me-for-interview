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