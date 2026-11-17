# TerraForge

Terraform project that deploys a web server on AWS using Infrastructure as Code.

## What it creates
- VPC with a public subnet
- Internet gateway and route table
- Security group (SSH only from my IP, HTTP open to all)
- EC2 instance (Amazon Linux 2023) with Nginx installed automatically through user data

## Tools used
Terraform, AWS (VPC, EC2, IAM, SSM), AWS CLI, Git, Nginx

## How to run
```bash
terraform init
terraform plan -var="my_ip=YOUR_IP/32"
terraform apply -var="my_ip=YOUR_IP/32"
```
Open the `server_ip` from the output in a browser (`http://<server_ip>`) to see the page.

To remove everything:
```bash
terraform destroy -var="my_ip=YOUR_IP/32"
```

## What I learned
- Writing and applying Terraform configuration (init, plan, apply, destroy)
- Setting up a basic AWS network (VPC, subnet, route table, security group)
- Using an IAM user and the AWS CLI
- Debugging an AWS Service Control Policy deny by switching the AMI lookup to an SSM parameter and using an allowed region
- Keeping state files and secrets out of Git with `.gitignore`

## Next steps
- Split the code into modules
- Store Terraform state remotely in S3
- Add a private subnet and a load balancer
- Run `terraform plan` automatically with GitHub Actions


## Output
![TerraForge live](images/terraforge-live.png)

![Destroy complete](images/terraforge-destroy-live.png)