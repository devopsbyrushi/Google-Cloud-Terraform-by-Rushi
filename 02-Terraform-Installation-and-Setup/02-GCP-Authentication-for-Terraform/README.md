
# 02 - GCP Authentication for Terraform

## Overview

In this lecture, we will configure **GCP authentication** so that Terraform can communicate with our Google Cloud environment.

---

## Step 01: Check Google Cloud CLI

```bash
gcloud version
````

---

## Step 02: Login to Google Cloud

```bash
gcloud auth login
```

---

## Step 03: Verify Authentication

```bash
gcloud auth list
```

---

## Step 04: Set GCP Project

```bash
gcloud config set project PROJECT_ID
```

Example:

```bash
gcloud config set project bankingproject2026
```

---

## Step 05: Verify Current Project

```bash
gcloud config get-value project
```

---

## Step 06: Configure Application Default Credentials

```bash
gcloud auth application-default login
```

A browser window will open. Sign in using the Google account that has access to the required GCP project.

---

## Step 07: Verify Application Default Credentials

```bash
gcloud auth application-default print-access-token
```

If an access token is displayed, Application Default Credentials are configured successfully.

---

## Authentication Flow

```text
Google Cloud Account
        ↓
gcloud auth login
        ↓
GCP Project
        ↓
Application Default Credentials
        ↓
Terraform
        ↓
GCP Resources
```

---

## Key Learning

Terraform needs authentication to communicate with GCP.

In this lecture, we configured Google Cloud authentication and Application Default Credentials required for working with Terraform.

---

## Next Step

**Section 03 → Terraform Basics**

