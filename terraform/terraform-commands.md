\# Terraform Commands



\## terraform init



Downloads:

\- Providers

\- Modules



Example:



```bash

terraform init

```



\---



\## terraform plan



Shows changes before execution.



Example:



```bash

terraform plan

```



Safe command.



No resources created.



\---



\## terraform apply



Creates or modifies infrastructure.



```bash

terraform apply

```



\---



\## terraform destroy



Deletes infrastructure.



```bash

terraform destroy

```



\---



\# Common Failure Scenarios



\## 1. Wrong AWS Credentials



Error:

Authentication failed.



Fix:

Verify AWS credentials.



\---



\## 2. State File Missing



Problem:

Terraform loses resource tracking.



Fix:

Restore state backup.



\---



\## 3. Manual Resource Changes



Problem:

Infrastructure drift.



Fix:

Run terraform plan and reconcile.



\---



\## 4. Concurrent Apply



Problem:

State corruption.



Fix:

DynamoDB locking.



\---



\## 5. Wrong Region



Problem:

Resources created in wrong location.



Fix:

Verify provider configuration.



\---



