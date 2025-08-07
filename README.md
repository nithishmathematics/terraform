# 🚀 DevOps Internship – Task 3: Infrastructure as Code (IaC) with Terraform

## 📌 Objective

Provision a local Docker container using **Terraform**, demonstrating Infrastructure as Code (IaC) principles. The task involved automating the deployment of an `nginx` container exposed at `http://localhost:8080` using declarative Terraform configuration.

---

## 💠 Tools Used

* [Terraform](https://www.terraform.io/)
* [Docker](https://www.docker.com/)
* Windows (Docker Desktop in Linux container mode)
* Git & GitHub

---

## 📂 Folder Structure

```
task-3/
├── main.tf                   # Terraform configuration
├── README.md                 # Project documentation
├── logs/                     # Execution logs
│   ├── init_log.txt
│   ├── plan_log.txt
│   ├── apply_log.txt
│   ├── docker_status.txt
│   └── destroy_log.txt

```

---

## ⚙️ What I Did

1. Wrote `main.tf` to define Docker provider, nginx image, and container.
2. Ran Terraform commands:

   * `terraform init`
   * `terraform plan`
   * `terraform apply -auto-approve`
   * Verified with `docker ps`
   * `terraform destroy -auto-approve`
3. Stored all command outputs under the `logs/` folder.
4. Pushed the complete project to GitHub for submission.

---

## 📝 Terraform Code (main.tf)

```hcl
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = false
}

resource "docker_container" "nginx_container" {
  name  = "nginx-container"
  image = docker_image.nginx.name
  ports {
    internal = 80
    external = 8080
  }
}
```

---

## 🔄 Output

After applying the configuration, the nginx server is accessible locally at:
➡️ **[http://localhost:8080](http://localhost:8080)**

Use `docker ps` to verify that the container is running.

---

## 📅 GitHub Commands Used

```bash
cd D:\internship\task-3

git init
git add .
git commit -m "Initial commit - Terraform Docker container"
git branch -M main
git remote add origin https://github.com/nithishmathematics/terraform.git
git push -u origin main
```

---

## 📉 Key Learnings

* Implemented complete Terraform lifecycle: `init`, `plan`, `apply`, and `destroy`
* Used Docker provider to manage container-based infrastructure
* Debugged and fixed common Terraform and Docker integration issues
* Practiced Git and GitHub workflows for version control and submission

---

## 📄 Submission

The GitHub repository link has been submitted through the internship task form.

```text
https://github.com/nithishmathematics/terraform
```
