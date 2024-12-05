```markdown
# Deploy a Three-Tier Architecture Using Terraform

## Project Overview

In this project, you or your group will be deploying a three-tier architecture using Terraform on AWS. The goal is to provision the necessary infrastructure that includes a **Web Tier**, **Application Tier**, and **Database Tier**, using Infrastructure-as-Code (IaC) principles. This project will help you practice provisioning and managing AWS resources using Terraform.

## Project Prerequisites

Before starting the project, ensure you have the following prerequisites:

- **AWS Account**: You will need an AWS account to create resources.
- **Terraform Installed**: Ensure you have Terraform installed. You can download it [here](https://www.terraform.io/downloads.html).
- **AWS CLI Configured**: You should have AWS CLI configured with your credentials. You can configure it using:
  ```bash
  aws configure
  ```
- **Basic Knowledge of Terraform**: Understanding how Terraform works and basic knowledge of AWS is required.

## Architecture Overview

This architecture will consist of three tiers:

1. **Web Tier**: A load-balanced set of EC2 instances serving static content via an Nginx web server.
2. **Application Tier**: EC2 instances running a simple application (e.g., Node.js, Python Flask).
3. **Database Tier**: A relational database instance (e.g., MySQL or PostgreSQL) running in an Amazon RDS instance.

## Instructions

### Step 1: Setup Terraform Configuration

1. **Create a new directory** for your project and navigate to it:
   ```bash
   mkdir three-tier-architecture
   cd three-tier-architecture
   ```

2. **Initialize Terraform** in the directory:
   ```bash
   terraform init
   ```

### Step 2: Define the VPC

1. **Create a new file** named `vpc.tf` to define the Virtual Private Cloud (VPC):
   - Define a **VPC** with public and private subnets.
   - Use `aws_vpc`, `aws_subnet`, and `aws_security_group` resources.

### Step 3: Set Up the Web Tier

1. **Create a new file** named `web-tier.tf` to define the web tier:
   - Define an **EC2 security group** that allows HTTP and SSH traffic.
   - Define an **Auto Scaling Group** for the EC2 instances.
   - Set up an **Elastic Load Balancer** (ELB) to distribute traffic across your EC2 instances.

### Step 4: Set Up the Application Tier

1. **Create a new file** named `app-tier.tf` to define the application tier:
   - Define an **EC2 security group** for application instances.
   - Define **EC2 instances** that run your application.
   - Make sure the application instances can only be accessed through the web tier.

### Step 5: Set Up the Database Tier

1. **Create a new file** named `db-tier.tf` to define the database tier:
   - Define an **RDS instance** (MySQL/PostgreSQL).
   - Create an **RDS security group** that allows access from the application tier.
   - Ensure the database tier is not directly accessible from the web tier.

### Step 6: Networking Configuration

1. **Create a new file** named `networking.tf` to configure the networking:
   - Set up **Route Tables** for public and private subnets.
   - Define **Internet Gateway** for internet access from the web tier.

### Step 7: Outputs and Variables

1. **Create a new file** named `outputs.tf` to define any outputs you want (e.g., the DNS name of the Load Balancer).

2. **Create a new file** named `variables.tf` to define any required variables like instance types, region, etc.

### Step 8: Apply the Configuration

1. **Validate the Terraform configuration** to ensure there are no syntax errors:
   ```bash
   terraform validate
   ```

2. **Plan the Terraform execution** to see what resources will be created:
   ```bash
   terraform plan
   ```

3. **Apply the configuration** to create the resources on AWS:
   ```bash
   terraform apply
   ```

4. When prompted, type `yes` to approve the changes.

### Step 9: Verify the Deployment

Once Terraform has successfully applied the configuration, you can verify the resources on the AWS Management Console:

- Check the **EC2 instances** in the web and application tiers.
- Ensure the **Elastic Load Balancer** is distributing traffic to the EC2 instances.
- Verify the **RDS database** is up and running in the database tier.

### Step 10: Clean Up Resources

After completing the project, don’t forget to clean up the resources to avoid unnecessary charges:

1. **Destroy the resources** using Terraform:
   ```bash
   terraform destroy
   ```

2. When prompted, type `yes` to confirm and destroy the resources.

---

## Notes

- Throughout the process, make sure you follow best practices for security, such as using security groups and IAM roles to limit access to your resources.
- Feel free to experiment and add new features, like setting up automatic backups for the database tier or adding more complex configurations for the EC2 instances in the application tier.

## Conclusion

By completing this project, you will have learned how to use Terraform to automate the deployment of a full-stack three-tier architecture on AWS. You will also have gained experience in working with VPCs, EC2, RDS, Auto Scaling, and Load Balancers, which are critical components in building cloud-based applications.

Good luck, and happy building!

