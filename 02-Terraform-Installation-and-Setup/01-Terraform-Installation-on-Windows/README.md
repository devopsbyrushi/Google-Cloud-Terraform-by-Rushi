````markdown
# 01 - Terraform Installation on Windows

## Overview

In this lecture, we will install **Terraform on Windows** and verify that Terraform is working correctly.

---

## Step 01: Create Terraform Folder

Create the following folder:

```text
C:\terraform
````

---

## Step 02: Download Terraform

Download the Terraform ZIP file for **Windows AMD64**.

Extract the ZIP file and place `terraform.exe` inside:

```text
C:\terraform
```

The final path should be:

```text
C:\terraform\terraform.exe
```

---

## Step 03: Add Terraform to PATH

Add the following folder to the Windows **Environment Variables → Path**:

```text
C:\terraform
```

> Add the folder path, not `terraform.exe`.

---

## Step 04: Verify Terraform Installation

Open **Command Prompt** or **PowerShell** and run:

```bash
terraform version
```

Terraform should display the installed version.

---

## Step 05: Verify GCP CLI

Check whether Google Cloud CLI is installed:

```bash
gcloud version
```



## Next Step



