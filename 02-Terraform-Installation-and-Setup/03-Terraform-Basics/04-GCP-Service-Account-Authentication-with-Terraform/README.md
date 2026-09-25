# 04 - GCP Service Account Authentication with Terraform

## Overview

In this lecture, we will configure Terraform to authenticate with Google Cloud using a **Service Account JSON key**.

We will create a Service Account key named:

```text
terraformkey.json
````

We will then use this key in our Terraform `provider` configuration and create a GCP Virtual Machine.

---

## Objective

In this lecture, we will:

* Create a Service Account key
* Store the JSON key in the Terraform project folder
* Configure the Google provider with the credentials
* Create a GCP VM using Terraform
* Understand how Terraform authenticates with GCP

---

## Step 01: Create a Service Account Key

Create a Service Account and generate a JSON key.

Save the downloaded key as:

```text
terraformkey.json
```

---

## Step 02: Place the Key in the Terraform Project

Place `terraformkey.json` in the same folder as `main.tf`.

```text
gcp-terraform-demo/
│
├── main.tf
└── terraformkey.json
```

---

## Step 03: Configure the Google Provider

Add the Service Account key to the Google provider:

```hcl
provider "google" {
  project     = "august2027"
  region      = "us-central1"
  zone        = "us-central1-a"
  credentials = file("terraformkey.json")
}
```

The important line is:

```hcl
credentials = file("terraformkey.json")
```

This tells Terraform to use the credentials stored in the JSON file to authenticate with Google Cloud.

---

## Step 04: Complete `main.tf`

Use the following complete configuration:

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

## Step 05: Initialize Terraform

```cmd
terraform init
```

---

## Step 06: Validate the Configuration

```cmd
terraform validate
```

---

## Step 07: Review the Plan

```cmd
terraform plan
```

---

## Step 08: Create the VM

```cmd
terraform apply
```

Enter:

```text
yes
```

---

## Step 09: Verify the VM

```cmd
gcloud compute instances list
```

---

## Step 10: Destroy the VM

After completing the lab:

```cmd
terraform destroy -auto-approve
```

---

## Important Security Note

The Service Account JSON key contains sensitive credentials.

**Never upload `terraformkey.json` to GitHub.**

Add the following to `.gitignore`:

```text
terraformkey.json
```

Recommended project structure:

```text
gcp-terraform-demo/
│
├── main.tf
├── terraformkey.json
└── .gitignore
```

The `terraformkey.json` file should remain only on your local machine.

---

## Key Learning

```text
Terraform
    ↓
Google Provider
    ↓
terraformkey.json
    ↓
Google Cloud Authentication
    ↓
GCP
```

We used a Service Account JSON key to authenticate Terraform with Google Cloud and created a GCP VM using Terraform.


