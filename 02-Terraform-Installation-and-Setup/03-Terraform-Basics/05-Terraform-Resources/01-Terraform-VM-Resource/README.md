
# 01 - Terraform Resource Block

## What is a Resource?

A **Resource** is an infrastructure component that Terraform can create and manage.

Examples:

- Virtual Machine
- VPC
- Database
- Storage Bucket
- Load Balancer

---

# Resource Block

Terraform uses a **resource block** to define an infrastructure resource.

### Basic Syntax

```hcl
resource "RESOURCE_TYPE" "LOCAL_RESOURCE_NAME" {

  ARGUMENTS

}
````

Example:

```hcl
resource "google_compute_instance" "my_vm" {

  name         = "my-vm"
  machine_type = "e2-micro"
  zone         = "us-central1-a"

}
```

---

# Understanding the Resource Block

Let's understand this line:

```hcl
resource "google_compute_instance" "my_vm" {
```

It has three important parts:

```text
resource
    ↓
Resource Type
    ↓
Local Resource Name
```

---

## 1. Resource

```hcl
resource
```

`resource` is a Terraform keyword.

It tells Terraform:

> We are going to define an infrastructure resource.

---

## 2. Resource Type

```hcl
google_compute_instance
```

This is the **Resource Type**.

It tells Terraform:

> What type of infrastructure do we want to create?

For example:

```text
google_compute_instance
```

represents a Google Cloud Compute Engine Virtual Machine.

Other examples:

```text
google_compute_network
```

represents a GCP VPC Network.

```text
google_sql_database_instance
```

represents a GCP Cloud SQL Database Instance.

---

## 3. Local Resource Name

```hcl
my_vm
```

This is the **Local Resource Name**.

It is the name Terraform uses to identify this resource inside our Terraform configuration.

We can choose this name.

For example:

```hcl
resource "google_compute_instance" "my_vm" {
```

or:

```hcl
resource "google_compute_instance" "web_server" {
```

Both are valid.

The resource type remains:

```text
google_compute_instance
```

Only the local name changes.

---

# Resource Type vs Local Resource Name

Consider:

```hcl
resource "google_compute_instance" "web_server" {
```

| Part                      | Meaning             |
| ------------------------- | ------------------- |
| `resource`                | Terraform keyword   |
| `google_compute_instance` | Resource Type       |
| `web_server`              | Local Resource Name |

Remember:

> **Resource Type = What to create**

> **Local Resource Name = What we call it inside Terraform**

---

# Resource Arguments

Inside the resource block, we define **arguments**.

Example:

```hcl
resource "google_compute_instance" "my_vm" {

  name         = "my-vm"
  machine_type = "e2-micro"
  zone         = "us-central1-a"

}
```

Here:

```text
name
machine_type
zone
```

are arguments.

Arguments are used to configure the resource.

---

# Simple Understanding

Think of a resource block like this:

```text
resource
   ↓
What type of resource?
   ↓
Resource Type
   ↓
What should Terraform call it?
   ↓
Local Resource Name
   ↓
How should it be configured?
   ↓
Arguments
```

---

# Complete Pattern

```hcl
resource "RESOURCE_TYPE" "LOCAL_RESOURCE_NAME" {

  argument1 = "value"
  argument2 = "value"
  argument3 = "value"

}
```

For example:

```hcl
resource "google_compute_instance" "my_vm" {

  name         = "my-vm"
  machine_type = "e2-micro"
  zone         = "us-central1-a"

}
```

---

# Common GCP Resource Types

| Resource Type                  | GCP Resource         |
| ------------------------------ | -------------------- |
| `google_compute_instance`      | Virtual Machine      |
| `google_compute_network`       | VPC Network          |
| `google_sql_database_instance` | Cloud SQL Database   |
| `google_storage_bucket`        | Cloud Storage Bucket |

---

# Important Points

### Resource Type

Defines **what Terraform should create**.

### Local Resource Name

Defines **how Terraform identifies the resource inside the code**.

### Arguments

Define **how the resource should be configured**.

---

# Remember

```text
Resource Block
      ↓
Resource Type
      ↓
Local Resource Name
      ↓
Arguments
```

Example:

```hcl
resource "google_compute_instance" "my_vm" {

  name         = "my-vm"
  machine_type = "e2-micro"
  zone         = "us-central1-a"

}
```

### In one line:

> **Resource Type tells Terraform WHAT to create, Local Resource Name identifies it inside Terraform, and Arguments define HOW it should be configured.**

---

# Next Lecture

In the next lecture, we will use the resource block to create our first:

**GCP Virtual Machine using Terraform**

