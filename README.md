# Azure Infrastructure Deployment with Terraform : Web Application Firewall (WAF)

This repository contains Terraform scripts to deploy and configure a sample Azure infrastructure. The project focuses on creating a scalable and secure environment for hosting web applications using Azure resources.

## Overview

Modern cloud-based applications often require a well-defined and scalable infrastructure. This Terraform project provides a set of configurations to deploy key Azure resources that form the backbone of such an environment. The infrastructure includes a Virtual Network, Subnets, Virtual Machines, an Application Gateway with Web Application Firewall (WAF), a Storage Account, Log Analytics Workspace, and a Key Vault.

## Prerequisites

Before using this Terraform configuration, ensure you have the following:

- [Terraform](https://www.terraform.io/downloads.html) installed
- An active Azure subscription and credentials
- Clone this repository: `git clone https://github.com/your-username/your-repo.git`

## Azure Resources Deployed

1. **Resource Group:**
   - Name: `myRG_KCR_NTL_PCH`
   - Location: `East US`

2. **Virtual Network:**
   - Name: `myVNet_KCR_NTL_PCH`
   - Address Space: `10.21.0.0/16`

3. **Subnets:**
   - Application Gateway Subnet: `myAGSubnet` (Address Range: `10.21.0.0/24`)
   - Backend Subnet: `myBackendSubnet` (Address Range: `10.21.1.0/24`)

4. **Public IP Address:**
   - Name: `myAGPublicIPAddress`
   - Allocation Method: `Static`
   - SKU: `Standard`

5. **Virtual Machines:**
   - Two Linux Virtual Machines with Nginx installed.

6. **Application Gateway:**
   - Name: `myAppGateway`
   - SKU: `WAF_v2`
   - Frontend Port: `httpPort` (Port: 80)
   - Backend Pool: `myBackendAddressPool`
   - WAF Configuration: Enabled with OWASP rules.

7. **Storage Account:**
   - Name: `kcrntlpcstorage`
   - Tier: `Standard`
   - Replication Type: `GRS`

8. **Log Analytics Workspace:**
   - Name: `KCRNTLPCHWorkspace`
   - SKU: `PerGB2018`

9. **Key Vault:**
   - Name: `KCRNTLPCHkeyvault`
   - Soft Delete Retention: `7 days`
   - SKU: `Standard`

10. **Diagnostic Setting:**
    - Name: `KCRNTLPCHDiagnostics`
    - Logs: Enabled for all logs
    - Metrics: Enabled for all metrics

## Terraform Configuration

The Terraform configuration is organized into modules, making it modular and easy to maintain. It follows best practices for infrastructure as code (IaC) and can be extended to include additional Azure services or customized based on specific project requirements.

## How to Use

1. **Set up Azure credentials:**

    ```bash
    az login
    ```

2. **Initialize Terraform:**

    ```bash
    terraform init
    ```

3. **Review the Terraform plan:**

    ```bash
    terraform plan
    ```

4. **Apply the Terraform configuration:**

    ```bash
    terraform apply
    ```

5. **Confirm the changes by typing `yes` when prompted.**

## Output

After successfully deploying the infrastructure, you can retrieve the private IP addresses of the virtual machines:

```bash
terraform output vm_private_ips
```