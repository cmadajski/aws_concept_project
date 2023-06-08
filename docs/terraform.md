# Terraform Docs

## What is Terraform

Terraform is an IaC (Infrastructure as Code) tool that allows you to provision cloud resources in a simple text format. Terraform uses HCL (Hashicorp Configuration Language) to define scripts. Check the [Terraform docs](https://developer.hashicorp.com/terraform/language) for more info.

# Terraform Basics

Before Terraform can do anything, we must first define what **providers** we will be using. Providers are simply the companies that are hosting the cloud resources that we wish to use. The primary 3 providers are:

- AWS (Amazon Web Services)
- GCP (Google Cloud Platform)
- Azure (Microsoft Azure)

Defining providers lets Terraform know what software packages need to be downloaded and login information for the cloud provider login. An example of a provider block:

```
provider "aws" {
    region = 'us-east-1"
    access_key = "******"
    secret_key = "******"
}
```

Once a provider has been defined, then we can start defining **resources**. Every service a cloud provider has to offer is considered a resource. An example of a resource block:

```
resource "aws_instance" "web-app-1" {
    ami           = "ami-053b0d53c279acc90"
    instance_type = "t2.micro"

    tags = {
        name = "Django Web App"
    }
}

```

## Variables

Terraform allows you to define variables that can be referenced in your main scripts. This can be useful for advanced scripting (variables can be passed in via command line options) or for keeping variables in a separate file for keeping things tidy. More info in the [variable docs](https://developer.hashicorp.com/terraform/language/values/variables).

To define variables in your main script file:

```
variable "my-name" {
    type        = string
    description = "the name of the person writing the script"
}
```

Variables can be defined in a separate file. There are many possible ways to do this, but the easiest in my opinion is to create a `terraform.tfvars` file that will be automatically loaded by Terraform during runtime.
