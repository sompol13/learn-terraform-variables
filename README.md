## Customize Terraform Configuration with Variables
In this tutorial, you will use Terraform to deploy a web application on AWS. The supporting infrastructure includes a VPC, load balancer, and EC2 instances. You will parameterize this configuration with Terraform input variables. Finally, you will interpolate variables into strings, use variables with functions, and use variable validation.

### Create infrastructure
- `terraform init`
- `terraform apply`

### Parameterize your configuration
- Edit the provider block in `main.tf` to use the new `aws_region` variable.
- Add a declaration for the `vpc_cidr_block` variable to variables.tf.
- Replace the hard-coded value for the VPC's CIDR block with a variable in `main.tf`.

### Reference
https://learn.hashicorp.com/tutorials/terraform/variables