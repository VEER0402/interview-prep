\# Terraform State



\## What is terraform.tfstate?



Terraform state file stores information about infrastructure created by Terraform.



Example:

\- EC2 ID

\- VPC ID

\- Security Group ID



\---



\## Why State File?



Terraform compares:



Desired State

vs

Actual State



using tfstate.



\---



\## Problem with Local State



If multiple engineers use Terraform:



\- State conflicts

\- Overwrites

\- Corruption risk



\---



\## Remote Backend



Store state remotely.



Common choice:

\- AWS S3



Example:



```hcl

terraform {

&#x20; backend "s3" {

&#x20;   bucket = "terraform-state-bucket"

&#x20;   key    = "prod/terraform.tfstate"

&#x20;   region = "ap-south-1"

&#x20; }

}

```



\---



\## State Locking



Problem:

Two engineers run terraform apply together.



Solution:

DynamoDB locking.



Benefits:

\- Prevents corruption

\- Prevents concurrent updates



