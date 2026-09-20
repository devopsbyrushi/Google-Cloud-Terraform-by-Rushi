
# 03 - Create Multiple GCP VMs Using Terraform

## Overview

In the previous lecture, we created a single GCP Virtual Machine using Terraform.

In this lecture, we will create **multiple GCP Virtual Machines using a single Terraform configuration**.

We will create two VMs with different zones and different disk sizes.

---

## Objective

Create two GCP Virtual Machines:

### VM-1

- VM Name: `vm-1`
- Machine Type: `e2-micro`
- Zone: `us-central1-a`
- Disk Size: `10 GB`
- OS: Ubuntu 24.04

### VM-2

- VM Name: `vm-2`
- Machine Type: `e2-micro`
- Zone: `us-east1-b`
- Disk Size: `12 GB`
- OS: Ubuntu 24.04

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
}
```

---

## Step 03: Create VM-1

VM-1 will be created in `us-central1-a` with a 10 GB boot disk.

```hcl
resource "google_compute_instance" "vm1" {
  name         = "vm-1"
  machine_type = "e2-micro"
  zone         = "us-central1-a"

  boot_disk {
    initialize_params {
      image = "ubuntu-os-cloud/ubuntu-2404-lts-amd64"
      size  = 10
    }
  }

  network_interface {
    network = "default"
  }
}
```

---

## Step 04: Create VM-2

VM-2 will be created in `us-east1-b` with a 12 GB boot disk.

```hcl
resource "google_compute_instance" "vm2" {
  name         = "vm-2"
  machine_type = "e2-micro"
  zone         = "us-east1-b"

  boot_disk {
    initialize_params {
      image = "ubuntu-os-cloud/ubuntu-2404-lts-amd64"
      size  = 12
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
}

resource "google_compute_instance" "vm1" {
  name         = "vm-1"
  machine_type = "e2-micro"
  zone         = "us-central1-a"

  boot_disk {
    initialize_params {
      image = "ubuntu-os-cloud/ubuntu-2404-lts-amd64"
      size  = 10
    }
  }

  network_interface {
    network = "default"
  }
}

resource "google_compute_instance" "vm2" {
  name         = "vm-2"
  machine_type = "e2-micro"
  zone         = "us-east1-b"

  boot_disk {
    initialize_params {
      image = "ubuntu-os-cloud/ubuntu-2404-lts-amd64"
      size  = 12
    }
  }

  network_interface {
    network = "default"
  }
}
```

---

## Step 05: Initialize Terraform

```cmd
terraform init
```

---

## Step 06: Validate Configuration

```cmd
terraform validate
```

---

## Step 07: Review the Execution Plan

```cmd
terraform plan
```

Terraform should show that **two VM resources** will be created.

---

## Step 08: Create Both VMs

```cmd
terraform apply
```

Enter:

```text
yes
```

Terraform will create both VMs.

---

## Step 09: Verify the VMs

```cmd
gcloud compute instances list
```

You should see:

```text
vm-1
vm-2
```

---

## Step 10: Destroy Both VMs

After completing the lab:

```cmd
terraform destroy
```

Enter:

```text
yes
```

Or use:

```cmd
terraform destroy -auto-approve
```

---

## Key Learning

In this lecture, we created **multiple GCP VMs using a single Terraform configuration**.

We learned that Terraform allows us to define multiple resources in the same `main.tf` file.

```text
main.tf
   ↓
┌───────────────┐
│ VM-1           │
│ us-central1-a  │
│ 10 GB          │
└───────────────┘

┌───────────────┐
│ VM-2           │
│ us-east1-b     │
│ 12 GB          │
└───────────────┘
```

---

## Important Concept

Each Terraform resource has its own **local name**.

```hcl
resource "google_compute_instance" "vm1"
```

```hcl
resource "google_compute_instance" "vm2"
```

Here:

```text
vm1 → Terraform local name for VM-1

vm2 → Terraform local name for VM-2
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
Two VMs Created
        ↓
terraform destroy
```

---

## Next Step

**04 - Terraform Variables**


