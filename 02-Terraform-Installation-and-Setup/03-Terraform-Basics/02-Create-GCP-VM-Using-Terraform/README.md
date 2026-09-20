# 02 - Create GCP VM Using Terraform

## Overview

In the previous lecture, we created our first Terraform project and configured the Google Cloud provider.

In this lecture, we will create our **first GCP Virtual Machine using Terraform**.

We will understand how Terraform uses a resource block to create infrastructure in Google Cloud.

---

## Objective

Create a single GCP Virtual Machine with:

- VM Name: `my-vm`
- Machine Type: `e2-micro`
- Zone: `us-central1-a`
- Operating System: Ubuntu 24.04
- Network: Default VPC Network

---

## Step 01: Create `main.tf`

Create a file named:

```text
main.tf
````

---

## Step 02: Add Terraform and Provider Configuration

```hcl
terraform {
  required_providers {
    google = {
      source  = "hashicorp/google"
      version = "8.3.0"
    }
  }
}

provider "google" {
  project = "august2027"
  region  = "us-central1"
  zone    = "us-central1-a"
}
```

---

## Step 03: Add GCP VM Resource

Add the following resource to `main.tf`:

```hcl
resource "google_compute_instance" "my_vm" {
  name         = "my-vm"
  machine_type = "e2-micro"
  zone         = "us-central1-a"

  boot_disk {
    initialize_params {
      image = "ubuntu-os-cloud/ubuntu-2404-lts-amd64"
    }
  }

  network_interface {
    network = "default"
  }
}
```

---

## Complete `main.tf`

```hcl
terraform {
  required_providers {
    google = {
      source  = "hashicorp/google"
      version = "8.3.0"
    }
  }
}

provider "google" {
  project = "august2027"
  region  = "us-central1"
  zone    = "us-central1-a"
}

resource "google_compute_instance" "my_vm" {
  name         = "my-vm"
  machine_type = "e2-micro"
  zone         = "us-central1-a"

  boot_disk {
    initialize_params {
      image = "ubuntu-os-cloud/ubuntu-2404-lts-amd64"
    }
  }

  network_interface {
    network = "default"
  }
}
```

---

## Step 04: Initialize Terraform

```cmd
terraform init
```

---

## Step 05: Validate Configuration

```cmd
terraform validate
```

---

## Step 06: Review the Execution Plan

```cmd
terraform plan
```

---

## Step 07: Create the VM

```cmd
terraform apply
```

Enter:

```text
yes
```

---

## Step 08: Verify the VM

```cmd
gcloud compute instances list
```

---

## Step 09: Destroy the VM

After completing the lab:

```cmd
terraform destroy
```

Enter:

```text
yes
```

Or destroy without confirmation:

```cmd
terraform destroy -auto-approve
```

---

## Terraform Workflow

```text
terraform init
        ↓
terraform validate
        ↓
terraform plan
        ↓
terraform apply
        ↓
GCP VM Created
        ↓
terraform destroy
```

---

## Key Learning

In this lecture, we created our first GCP VM using Terraform.

We learned how to:

* Define a GCP provider
* Define a Terraform resource
* Configure a Compute Engine VM
* Initialize Terraform
* Validate Terraform configuration
* Preview changes using `terraform plan`
* Create infrastructure using `terraform apply`
* Delete infrastructure using `terraform destroy`

---

## Next Step

**03 - Create Multiple GCP VMs Using Terraform**

