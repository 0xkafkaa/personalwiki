# Terraform
Terraform is a tool to manage infrastructure as code. It enables the provisioning and management of cloud and on-premises resources using a declarative configuration language, making it easier to automate and maintain infrastructure across multiple platforms.

![terraform-1](/terraform-1.png)
## Basic Commands
![terraform-2](/terraform-2.png)

![terraform-3](/terraform-3.png)

![terraform-4](/terraform-4.png)

![terraform-5](/terraform-5.png)

![terraform-6](/terraform-6.png)
## Setup an EC2 instance with terraform
``` tf
provider "aws" {
  region = "ap-south-1"
  access_key = "XXXXXXXXXXXXX"
  secret_key = "XXXXXXXXXXXXX"
}

resource "aws_instance" "demo_ec2" {  
  ami = "ami-0024b53e5fc2f4fad"
  instance_type = "t2.nano"

  tags = {
    Name = "Terraform EC2"
  }
}

```
Few things which required troubleshooting were the following:
- The access keys from the User created from IAM Identity Center were not working for some reason. Hence, created a user from IAM and applied the credentials generated from there.
- The image of the instance should be present in the region else you will get an error 'instance not found'.
- The architecture of the instance should support the architecture of the image. One should not be arm64 and the other should not be x86.
