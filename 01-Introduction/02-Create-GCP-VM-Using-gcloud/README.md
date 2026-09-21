
# 02 - Create GCP VM Using gcloud

## Overview

In this section, we will learn how to create and manage a Google Cloud Compute Engine Virtual Machine (VM) using the `gcloud` command-line tool.

Instead of creating the VM manually through the Google Cloud Console, we can use a command to create it directly from the terminal.

---

## Objective

By the end of this section, we will learn how to:

- Check the current GCP project
- Set the GCP project
- Create a Compute Engine VM using `gcloud`
- Understand the `gcloud` command
- Verify the VM
- Delete the VM
- Delete the VM without confirmation

---

# Step-01: Check the Current GCP Project

Before creating a VM, we should know which Google Cloud project is currently selected.

Run:

```bash
gcloud config get-value project
````

This displays the currently configured GCP project.

### Example

```text
bankingproject2026
```

> Always verify the project before creating Cloud resources. This helps avoid creating resources in the wrong project.

---

# Step-02: Set the GCP Project

If the required project is not currently selected, set it using:

```bash
gcloud config set project PROJECT_ID
```

### Example

```bash
gcloud config set project bankingproject2026
```

Verify again:

```bash
gcloud config get-value project
```

---

# Step-03: Understand the gcloud Command

The `gcloud` command-line tool allows us to create and manage Google Cloud resources directly from the command line.

Instead of performing the following activities manually:

```text
Open Google Cloud Console
        ↓
Go to Compute Engine
        ↓
Create VM
        ↓
Select Configuration
        ↓
Create VM
```

we can use a command:

```text
gcloud command
     ↓
VM Created
```

---

# Step-04: Create a GCP VM

Use the following command:

```bash
gcloud compute instances create my-vm \
  --zone=us-central1-a \
  --machine-type=e2-micro
```

After successful execution, Google Cloud creates the VM.

---

# Step-05: Understand the Command

Let's understand each part of the command.

```bash
gcloud compute instances create my-vm \
  --zone=us-central1-a \
  --machine-type=e2-micro
```

| Command          | Meaning                           |
| ---------------- | --------------------------------- |
| `gcloud`         | Google Cloud command-line tool    |
| `compute`        | Work with Compute Engine          |
| `instances`      | Manage VM instances               |
| `create`         | Create a new VM                   |
| `my-vm`          | Name of the VM                    |
| `--zone`         | Zone where the VM will be created |
| `--machine-type` | Machine type / VM size            |

### Simple Understanding

The command means:

> Create a Compute Engine VM named `my-vm` in the `us-central1-a` zone using the `e2-micro` machine type.

---

# Step-06: Verify the VM

After creating the VM, verify it using:

```bash
gcloud compute instances list
```

This displays the Compute Engine VM instances available in the selected project.

You should see your VM:

```text
my-vm
```

with its zone, machine type, internal IP, external IP, and status.

---

# Step-07: Delete the VM

After completing the practice, we can delete the VM.

Use:

```bash
gcloud compute instances delete my-vm \
  --zone=us-central1-a
```

Google Cloud will ask for confirmation.

Enter:

```text
Y
```

to continue.

---

# Step-08: Delete the VM Without Confirmation

We can also use the `--quiet` option.

```bash
gcloud compute instances delete my-vm \
  --zone=us-central1-a \
  --quiet
```

The `--quiet` option skips the interactive confirmation.

---

# Complete Command Flow

The complete workflow is:

```text
Check Project
     ↓
Set Project
     ↓
Create VM
     ↓
Verify VM
     ↓
Delete VM
```

### Commands

```bash
# Check current project
gcloud config get-value project

# Set project
gcloud config set project PROJECT_ID

# Create VM
gcloud compute instances create my-vm \
  --zone=us-central1-a \
  --machine-type=e2-micro

# Verify VM
gcloud compute instances list

# Delete VM
gcloud compute instances delete my-vm \
  --zone=us-central1-a
```

---

# Key Takeaways

* `gcloud` allows us to manage Google Cloud resources from the command line.
* `gcloud compute instances create` creates a Compute Engine VM.
* `--zone` specifies where the VM is created.
* `--machine-type` specifies the VM machine type.
* `gcloud compute instances list` helps us verify VMs.
* `gcloud compute instances delete` removes a VM.
* `--quiet` can be used to skip confirmation.

---

## Next Step

In the next section, we will learn how to create **multiple GCP VMs using gcloud commands**.
