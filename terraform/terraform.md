\# Terraform Basics



\## What is Terraform?



Terraform is an Infrastructure as Code (IaC) tool developed by HashiCorp.



It is used to create, update and manage infrastructure using code.



Examples:

\- EC2

\- VPC

\- S3

\- RDS

\- EKS



\---



\## Why Terraform?



Before Terraform:

\- Manual infrastructure creation

\- Human errors

\- Difficult to reproduce environments



With Terraform:

\- Infrastructure is version controlled

\- Repeatable deployments

\- Automation



\---



\## Terraform Workflow



1\. Write Code

2\. terraform init

3\. terraform plan

4\. terraform apply

5\. terraform destroy



\---



\## Main Components



\### Provider



Connects Terraform to cloud provider.



Example:



```hcl

provider "aws" {

&#x20; region = "ap-south-1"

}

```



\### Resource



Actual infrastructure.



```hcl

resource "aws\_instance" "web" {

&#x20; ami           = "ami-123456"

&#x20; instance\_type = "t2.micro"

}

```



\---



