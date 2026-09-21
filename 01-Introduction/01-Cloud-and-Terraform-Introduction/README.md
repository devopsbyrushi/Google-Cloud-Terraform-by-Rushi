
# 01 - Cloud and Terraform Introduction

## Overview

In this section, we will understand why Terraform is important when working with Cloud platforms such as AWS, Azure, and Google Cloud.

In real-time organizations, infrastructure is rarely managed manually when working across multiple projects and environments. Repetitive activities can become time-consuming and difficult to maintain.

Terraform helps us automate Cloud infrastructure using Infrastructure as Code (IaC).

---

## What We Will Learn

- Why Cloud and Terraform are used together
- Challenges of managing multiple Cloud projects manually
- Different methods of creating Cloud infrastructure
- Web Console (GUI)
- gcloud command-line tools
- Terraform
- Why Infrastructure as Code is important
- How Terraform helps with automation, consistency, scalability, and versioning

---

## Why Cloud and Terraform?

When learning Cloud platforms such as:

- AWS
- Azure
- Google Cloud

it is important to understand Terraform as an Infrastructure as Code tool.

In real-time organizations, we may work on a single project or multiple projects.

Each project can have different requirements such as:

- Virtual Machines
- Databases
- VPC / Networks
- Security and firewall configurations
- Other Cloud resources

When the same type of activity needs to be performed repeatedly across multiple projects, doing everything manually becomes time-consuming and difficult to maintain.

### Example

```text
Project 1 → Create Infrastructure
Project 2 → Create the same/similar Infrastructure
Project 3 → Create the same/similar Infrastructure
````

Instead of repeating these activities manually, we can define the infrastructure as code and automate the provisioning process using Terraform.

---

## Important Concept

> Before automating infrastructure, we should understand how to create and manage that infrastructure manually.

Once we understand the manual process, we can identify the steps and automate them using Terraform.

```text
Understand Manual Process
        ↓
Identify Repetitive Activities
        ↓
Define Infrastructure as Code
        ↓
Automate Using Terraform
```

---

## Methods of Creating Cloud Infrastructure

There are three common approaches we will understand in this training:

| Method          | Approach               |
| --------------- | ---------------------- |
| Web Console     | GUI-based              |
| gcloud Commands | Command-line based     |
| Terraform       | Infrastructure as Code |

### 1. Web Console

Cloud resources can be created manually using the Google Cloud Console.

This is useful for learning and understanding the Cloud platform.

### 2. gcloud Commands

The Google Cloud CLI allows us to create and manage Cloud resources from the command line.

For example, we can create a VM using:

```bash
gcloud compute instances create my-vm \
  --zone=us-central1-a \
  --machine-type=e2-micro
```

### 3. Terraform

Terraform allows us to define Cloud infrastructure as code.

Instead of repeatedly creating resources manually, we can create reusable Terraform configurations.

---

## Manual Infrastructure vs Terraform

| Manual Work             | Terraform          |
| ----------------------- | ------------------ |
| Repetitive              | Reusable           |
| Error-Prone             | Consistent         |
| Time-Consuming          | Automated          |
| Hard to Scale           | Scalable           |
| No Versioning           | Version-Controlled |
| Hard to Track           | Trackable          |
| Manual Changes          | Code Changes       |
| Difficult Collaboration | Team Collaboration |
| Hard to Rebuild         | Reproducible       |
| Console-Based           | Code-Based         |

---

## Key Takeaway

Cloud knowledge and Infrastructure as Code are important skills for modern Cloud infrastructure management.

The learning path is:

```text
Cloud
  ↓
Understand Infrastructure
  ↓
Manual Configuration
  ↓
gcloud Commands
  ↓
Automation
  ↓
Terraform
  ↓
Reusable & Version-Controlled Infrastructure
```

---

## Next Step

In the next section, we will create a Google Cloud VM using the `gcloud` command-line tool.

