

# Container Image Vulnerability Scanning Using Trivy

## Overview

Trivy is a lightweight and powerful security scanner used to detect vulnerabilities (CVEs) in container images. It scans both operating system packages and application dependencies to identify known security issues.

This document explains how to install Trivy and scan a Docker image for vulnerabilities.

---

## 1. Install Trivy

### Step 1: Update system packages

```bash
sudo apt update
```

### Step 2: Install required utility

```bash
sudo apt install wget -y
```

### Step 3: Download Trivy package

```bash
wget https://github.com/aquasecurity/trivy/releases/latest/download/trivy_0.50.1_Linux-64bit.deb
```

### Step 4: Install Trivy

```bash
sudo dpkg -i trivy_0.50.1_Linux-64bit.deb
```

---

## 2. Verify Installation

Confirm that Trivy is installed correctly:

```bash
trivy --version
```

Expected output will display the installed Trivy version.

---

## 3. Pull a Sample Docker Image

Before scanning, pull a container image from Docker Hub:

```bash
docker pull nginx:latest
```

This downloads the latest Nginx container image to your local system.

---

## 4. Scan Docker Image for Vulnerabilities

Run the following command to scan the image:

```bash
trivy image nginx:latest
```

---

## 5. What Trivy Scans

When scanning a container image, Trivy analyzes:

* **Operating System Packages**

  * Example: Alpine, Debian, Ubuntu packages
* **Application Dependencies**

  * Libraries and runtime dependencies inside the image
* **Known Vulnerabilities (CVEs)**

  * Matches against the Trivy vulnerability database

---

## 6. Output Information

The scan report typically includes:

* Vulnerability ID (CVE)
* Severity level (LOW, MEDIUM, HIGH, CRITICAL)
* Installed version
* Fixed version (if available)
* Package name
* Description of vulnerability

---

## Summary

Trivy provides an efficient way to secure container images by detecting vulnerabilities early in the development lifecycle. It is widely used in DevSecOps pipelines for continuous security scanning.

---

