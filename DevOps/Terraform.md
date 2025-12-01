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