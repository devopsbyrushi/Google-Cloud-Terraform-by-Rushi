````markdown
# 01 - Create First Terraform Project

## Overview

In this lecture, we will create our first Terraform project on **Windows** and configure the Google Cloud provider.

---

## Step 01: Create Project Folder

Create the following folder on your Windows Desktop:

```text
Desktop
└── gcp-terraform-demo
````

---

## Step 02: Open Command Prompt

Open **Command Prompt** and navigate to the project folder:

```cmd
cd %USERPROFILE%\Desktop\gcp-terraform-demo
```

---

## Step 03: Open Project in VS Code

```cmd
code .
```

---

## Step 04: Create Terraform Configuration File

Create the following file inside the project folder:

```text
main.tf
```

---

## Step 05: Add Google Cloud Provider

Add the following configuration to `main.tf`:

```hcl
terraform {
  required_providers {
    google = {
      source  = "hashicorp/google"
      version = "~> 7.0"
    }
  }
}

provider "google" {
  project = "bankingproject2026"
  region  = "us-central1"
  zone    = "us-central1-a"
}
```

---

## Step 06: Initialize Terraform

Open the terminal in VS Code and run:

```cmd
terraform init
```

---

## Step 07: Validate Terraform Configuration

```cmd
terraform validate
```

---

## Key Learning

In this lecture, we created our first Terraform project on Windows.

```text
Windows Desktop
      ↓
gcp-terraform-demo
      ↓
main.tf
      ↓
Google Cloud Provider
      ↓
terraform init
      ↓
terraform validate
```

---

## Next Step

**02 - Terraform Configuration and Provider**
