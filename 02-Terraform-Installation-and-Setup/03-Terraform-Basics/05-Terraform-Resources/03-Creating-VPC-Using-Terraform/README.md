# 03 - Creating VPC Using Terraform

## Objective

In this lecture, we will create a **Google Cloud VPC Network** using Terraform.

---

# GCP VPC Resource

To create a Google Cloud VPC Network, we use:

```hcl
google_compute_network
````

---

# Resource Block

```hcl
resource "google_compute_network" "my_vpc" {
```

Here:

```text
google_compute_network → Resource Type
my_vpc                 → Local Resource Name
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
  credentials = file("terraformkey.json")
}

resource "google_compute_network" "my_vpc" {
  name                    = "resource-vpc"
  auto_create_subnetworks = true
}
```

---

# Understanding the VPC Resource

## Resource Type

```hcl
google_compute_network
```

This represents a:

```text
Google Cloud VPC Network
```

---

## Local Resource Name

```hcl
my_vpc
```

This is the name Terraform uses to identify the VPC inside our configuration.

---

## VPC Name

```hcl
name = "resource-vpc"
```

This is the actual VPC name that will appear in Google Cloud.

So:

```text
my_vpc
   ↓
Terraform local name

resource-vpc
   ↓
Actual GCP VPC name
```

---

## Auto Create Subnetworks

```hcl
auto_create_subnetworks = true
```

This allows Google Cloud to automatically create subnetworks for the VPC.

For this beginner example, we are keeping it simple with:

```text
true
```

---

# Create the VPC

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

# Verify the VPC

Run:

```cmd
gcloud compute networks list
```

You should see:

```text
resource-vpc
```

---

# Delete the VPC

After completing the practice:

```cmd
terraform destroy -auto-approve
```

---

# Practice Task

Create another VPC with:

```text
VPC Name : practice-vpc
```

Use:

```hcl
resource "google_compute_network" "practice_vpc" {
```

Set:

```hcl
auto_create_subnetworks = true
```

---

# Key Learning

We created a GCP VPC using the Terraform resource:

```hcl
google_compute_network
```

The basic flow is:

```text
Terraform
    ↓
google_compute_network
    ↓
GCP VPC Network
```

