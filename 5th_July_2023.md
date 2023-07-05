## 5TH JULY 2023

- Terraform is used to monitor changes , earlier if some changes are made in aws like changing instance type or any other thing it was not monitored but with terraform it is monitored and chances of making mistakes are reduced.
- for eg. we want to make 15 same instance types in different regions it will be difficult to do this manually but with terraform it is done easily.
- Terraform is a declarative tool.
- Declarative tool vs Imperative tool
- COMMANDS:
    - terraform init // done only once
    - terraform plan
    - terraform apply
- Terragrunt helps you to work with terraform configuration.
- Consistency should always be meant in DEV and PROD environment.
- Make use of Terraform Documentation to understand any concept. It has very descriptive and good documentation.
- Terraform Output allows you to display outputs for someone else for example Jenkins.
- What is .tfstate file?--->Basically how will terraform know app_server is information of some instance. it holds this information in .tfstate file. If you loose this file terraform is of no use. **.tfstate** file includes all your cloud means contains sensitive data hence don't commit and push this.
- Check about Race Condition in OS.
