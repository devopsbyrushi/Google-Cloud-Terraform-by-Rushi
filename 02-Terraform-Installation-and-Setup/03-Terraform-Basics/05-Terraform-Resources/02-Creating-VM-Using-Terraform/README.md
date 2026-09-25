# 02 - Creating VM Using Terraform

## Objective

In this lecture, we will create a **Google Cloud Virtual Machine (VM)** using Terraform.

---

# GCP VM Resource

To create a Google Cloud VM, Terraform provides the following resource type:

```hcl
google_compute_instance
````

---

# Resource Block

```hcl
resource "google_compute_instance" "my_vm" {
```

Here:

```text
google_compute_instance → Resource Type
my_vm                   → Local Resource Name
```

---

# Complete Terraform Configuration

Create a file:

```text
main.tf
```

Add:

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
  project     = "august2027"
  region      = "us-central1"
  zone        = "us-central1-a"
  credentials = file("terraformkey.json")
}

resource "google_compute_instance" "my_vm" {
  name         = "resource-vm"
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

# Understanding the VM Resource

## Resource Type

```hcl
google_compute_instance
```

This represents a:

```text
Google Cloud Compute Engine Virtual Machine
```

---

## Local Resource Name

```hcl
my_vm
```

This is the name Terraform uses to identify the VM inside our configuration.

---

## VM Name

```hcl
name = "resource-vm"
```

This is the actual VM name that will appear in Google Cloud.

Notice the difference:

```text
my_vm
   ↓
Terraform local name

resource-vm
   ↓
Actual GCP VM name
```

---

## Machine Type

```hcl
machine_type = "e2-micro"
```

Defines the machine type of the VM.

For our practice lab, we are using:

```text
e2-micro
```

---

## Zone

```hcl
zone = "us-central1-a"
```

Defines the zone where the VM will be created.

---

## Boot Disk

```hcl
boot_disk {
  initialize_params {
    image = "ubuntu-os-cloud/ubuntu-2404-lts-amd64"
  }
}
```

This defines the VM's boot disk and operating system.

We are using:

```text
Ubuntu 24.04
```

---

## Network Interface

```hcl
network_interface {
  network = "default"
}
```

This connects the VM to the default VPC network.

---

# Create the VM

We already learned the Terraform workflow in the previous lectures.

Run:

```cmd
terraform init
```

```cmd
terraform plan
```

```cmd
terraform apply -auto-approve
```

---

# Verify the VM

Run:

```cmd
gcloud compute instances list
```

You should see:

```text
resource-vm
```

---

# Delete the VM

After completing the practice:

```cmd
terraform destroy -auto-approve
```

---

# Practice Task

Create another VM with the following details:

```text
VM Name      : practice-vm
Machine Type : e2-micro
Zone         : us-central1-a
OS           : Ubuntu 24.04
Network      : default
```

Use:

```hcl
resource "google_compute_instance" "practice_vm" {
```

---

# Key Learning

We created a GCP VM using the Terraform resource:

```hcl
google_compute_instance
```

The basic flow is:

```text
Terraform
    ↓
google_compute_instance
    ↓
GCP Compute Engine VM
```


└── README.md
````
