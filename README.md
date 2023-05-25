# AWS Concept Project

The premise of this project is to create a generic Django app that runs using various cloud services.
This will showcase my ability to use cloud-specific tools that have become increasingly relevant 
due to the adoption of cloud services in most enterprise environments.

## Tech Stack

All of the cloud services will be provided by AWS:

- S3 Buckets (static files)
- EC2 instances (Django app)
- RDS (database)
- SQS (queue for Google Bard queries)
- CloudWatch (performance monitoring)

Additional cloud tools will be leveraged to simplify deployment and improve compliance:

- Ansible (manage all EC2 instances programmatically)
- Terraform (provision all AWS services via IaC)

## Application Checklist

- [ ] Configure AWS Account
- [ ] Install and Configure Terraform on client machine
- [ ] Create basic design documentation to outline architecture
- [ ] Use Terraform to Provision AWS resources
- [ ] Create Django app MVP with user auth
- [ ] Move all static files to S3 bucket
