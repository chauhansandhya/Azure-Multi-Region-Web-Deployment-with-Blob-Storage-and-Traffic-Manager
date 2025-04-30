# Azure-Multi-Region-Web-Deployment-with-Blob-Storage-and-Traffic-Manager

This project demonstrates how to deploy a web application with region redundancy, custom routing, file upload capability, and centralized traffic management using Microsoft Azure services.

---

## 🌐 Overview

The application consists of:
- A **Home Page** (VM2)
- An **Upload Page** (VM1), which uploads files to Azure Blob Storage
- A custom **Error Page** (`error.html`) for HTTP 403 and 502, hosted in Azure Blob Storage

All services are deployed across **two Azure regions**: Central US and West US.

---

## 🛠️ Technologies Used

- **Azure Virtual Machines (VMs)**
- **Azure Blob Storage** (for static hosting and file uploads)
- **Azure Application Gateway** (for URL-based routing and error redirection)
- **Azure Traffic Manager** (for global traffic distribution)
- **Azure Virtual Network (VNet) Peering**
- **Python**, **Shell Scripts**
- **Git**, **GitHub**

---

## ⚙️ Architecture Workflow

1. Clone GitHub repo:  
   `https://github.com/azcloudberg/azproject`

2. Run deployment scripts on each VM:
   - **VM1**: `./vm1.sh` – Deploys upload page  
   - **VM2**: `./vm2.sh` – Deploys home page

3. Edit `config.py` on VM1 to configure Blob Storage details.

4. Run the upload app:  
   `sudo python3 app.py`

5. Configure Application Gateway routing:
   - `/` → VM2 (Home Page)
   - `/upload` → VM1 (Upload Page)
   - 403/502 → Static error.html in Azure Blob Storage

6. Enable **VNet-to-VNet Peering** between both regions.

7. Configure **Azure Traffic Manager** to point to both Application Gateways for regional traffic distribution.

---

## 📦 Storage Configuration

- Create a **Blob Storage Account** with:
  - Static website hosting for `error.html`
  - A container named `upload` for file uploads

