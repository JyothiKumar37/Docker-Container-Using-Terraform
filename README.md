Terraform Docker Container Provisioning

This project demonstrates Infrastructure as Code (IaC) using Terraform to provision a Docker container locally.

Project Structure
terraform-docker/
├── main.tf               # Terraform configuration file
├── execution.log         # Terraform execution logs
└── README.md             # Project documentation

Workflow

The Terraform workflow includes the following steps:

Initialize Terraform:

terraform init

Plan the infrastructure:

terraform plan


Apply the configuration:

terraform apply -auto-approve


Verify container is running:

docker ps


Inspect Terraform state

terraform state list


Destroy infrastructure

terraform destroy -auto-approve

Terraform Configuration Overview

Uses Docker provider to pull an image and run a container.

Example main.tf:

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = false
}

resource "docker_container" "nginx" {
  name  = "nginx_container"
  image = docker_image.nginx.latest
  ports {
    internal = 80
    external = 8080
  }
}


Optional files: variables.tf, outputs.tf for modularity.

Execution Logs

All Terraform executions should be captured in execution.log:

terraform init
terraform plan
terraform apply -auto-approve
docker ps
terraform state list
terraform destroy -auto-approve




Outcome

Fully automated provisioning of Docker containers using Terraform.

Demonstrates IaC principles: declarative, repeatable, and version-controlled infrastructure.
