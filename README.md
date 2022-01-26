## Customize Terraform Configuration with Variables
In this tutorial, you will use Terraform to deploy a web application on AWS. The supporting infrastructure includes a VPC, load balancer, and EC2 instances. You will parameterize this configuration with Terraform input variables. Finally, you will interpolate variables into strings, use variables with functions, and use variable validation.

![Load Balancer](https://user-images.githubusercontent.com/33342822/151195260-363f3f3d-5d9c-44eb-8ced-dc42fa8b34aa.png)

### Create infrastructure
- `terraform init`
- `terraform apply`

### Parameterize your configuration
- Edit the provider block in `main.tf` to use the new `aws_region` variable.
- Add a declaration for the `vpc_cidr_block` variable to variables.tf.
- Replace the hard-coded value for the VPC's CIDR block with a variable in `main.tf`.

### Set the number of instances
- Use a number type to define the number of instances supported by this configuration. Add the following to `variables.tf`.
- Update EC2 instances to use the `instance_count` variable in `main.tf`.

### Toggle VPN gateway support
- Use a `bool` type variable to control whether your VPC is configured with a VPN gateway. Add the following to `variables.tf`.
- Use this new variable in your VPC configuration by editing `main.tf` as follows.

### List public and private subnets
- `terraform console`
- Refer to the variable by name to return the entire list.
- `terraform console`
- `var.private_subnet_cidr_blocks`
- Retrieve the second element from the list by index with square brackets.
- `var.private_subnet_cidr_blocks[1]`
- Now use the slice() function to return the first three elements from the list.
- `slice(var.private_subnet_cidr_blocks, 0, 3)`

*Leave the console by typing exit or pressing Control-D.*

- Now use the slice function to extract a subset of the cidr block lists in `main.tf` when defining your VPC's public and private subnet configuration.

### Map resource tags
- Declare a new `map` variable for resource tags in `variables.tf`.
- `terraform console`
- Retrieve the value of the `environment` key from the `resource_tags` map.
- `var.resource_tags["environment"]`
- Now, replace the hard coded tags in `main.tf` with references to the new variable.

### Assign values when prompted
- Add a new variable without a default value to `variables.tf`.
- Replace the reference to the EC2 instance type in `main.tf`.

### Assign values with a `terraform.tfvars` file
- Create a file named `terraform.tfvars` with the following contents.

### Interpolate variables in strings
- Update the names of the security groups to use the project and environment values from the `resource_tags` map.
- `terraform apply`

### Validate variables
- `terraform apply -var='resource_tags={project="my-project",environment="development"}'`

### Reference
https://learn.hashicorp.com/tutorials/terraform/variables
