
# 04 - Creating Database Using Terraform

## Objective

In this lecture, we will create a **Google Cloud SQL Database Instance** using Terraform.

---

# GCP Database Resource

To create a Google Cloud SQL Database Instance, we use:

```hcl
google_sql_database_instance
````

---

# Resource Block

```hcl
resource "google_sql_database_instance" "my_database" {
```

Here:

```text
google_sql_database_instance → Resource Type
my_database                 → Local Resource Name
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

resource "google_sql_database_instance" "my_database" {
  name             = "resource-database"
  database_version = "MYSQL_8_0"
  region           = "us-central1"

  settings {
    tier = "db-f1-micro"
  }

  deletion_protection = false
}
```

---

# Understanding the Database Resource

## Resource Type

```hcl
google_sql_database_instance
```

This represents a:

```text
Google Cloud SQL Database Instance
```

---

## Local Resource Name

```hcl
my_database
```

This is the name Terraform uses to identify the database inside our configuration.

---

## Database Name

```hcl
name = "resource-database"
```

This is the actual Cloud SQL instance name in Google Cloud.

So:

```text
my_database
    ↓
Terraform local name

resource-database
    ↓
Actual GCP database instance name
```

---

## Database Version

```hcl
database_version = "MYSQL_8_0"
```

This specifies the database engine and version.

Here we are using:

```text
MySQL 8.0
```

---

## Region

```hcl
region = "us-central1"
```

Defines where the Cloud SQL instance will be created.

---

## Database Tier

```hcl
settings {
  tier = "db-f1-micro"
}
```

The `tier` defines the machine configuration for the Cloud SQL instance.

For this practice example:

```text
db-f1-micro
```

---

## Deletion Protection

```hcl
deletion_protection = false
```

This allows Terraform to destroy the database during our practice.

> Use deletion protection carefully for real production databases.

---

# Create the Database

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

# Verify the Database

Run:

```cmd
gcloud sql instances list
```

You should see:

```text
resource-database
```

---

# Delete the Database

After completing the practice:

```cmd
terraform destroy -auto-approve
```

---

# Practice Task

Create another Cloud SQL instance with:

```text
Database Name : practice-database
Database      : MySQL 8.0
Region        : us-central1
Tier          : db-f1-micro
```

Use:

```hcl
resource "google_sql_database_instance" "practice_database" {
```

---

# Key Learning

We created a GCP Cloud SQL Database using the Terraform resource:

```hcl
google_sql_database_instance
```

The basic flow is:

```text
Terraform
    ↓
google_sql_database_instance
    ↓
GCP Cloud SQL Database
```

---

# Terraform Resources Covered

We have now learned three important GCP resources:

```text
google_compute_instance
        ↓
Virtual Machine
```

```text
google_compute_network
        ↓
VPC Network
```

```text
google_sql_database_instance
        ↓
Cloud SQL Database
```

---

