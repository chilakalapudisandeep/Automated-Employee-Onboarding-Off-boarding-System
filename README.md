# 🚀 Automated Employee Onboarding & Off boarding System

[![ServiceNow](https://img.shields.io/badge/ServiceNow-Washington%20DC-green?style=for-the-badge&logo=servicenow&logoColor=white)](https://www.servicenow.com/)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)](https://github.com/)

An enterprise-grade ServiceNow custom application designed to automate and streamline the employee lifecycle. This system orchestrates HR requests, automates approval workflows, auto-provisions catalog tasks to cross-functional teams, tracks performance via Service Level Agreements (SLAs), and visualizes key metrics on custom Dashboards.

---

## 📌 Table of Contents

- [🔍 Project Description](#-project-description)
- [✨ Key Features](#-key-features)
- [🧩 ServiceNow Implementation Details](#-servicenow-implementation-details)
- [📐 System Architecture & Workflow](#-system-architecture--workflow)
- [📁 Repository Folder Structure](#-repository-folder-structure)
- [📸 Screenshots & Visuals](#-screenshots--visuals)
- [👥 Team & Roles](#-team--roles)

---

## 🔍 Project Description

In modern organizations, onboarding new hires and offboarding departing employees are highly manual, error-prone processes. This project solves these challenges by implementing an automated **Employee Lifecycle Management** system on the **ServiceNow** platform. The solution provides a unified Service Catalog interface for HR, which triggers a robust, automated workflow designed using **Flow Designer**.

---

## ✨ Key Features

*   **Self-Service Catalog Items:** Forms for Employee Onboarding and Employee Offboarding accessible via the ServiceNow Service Portal.
*   **Automated Lifecycle Record:** Auto-generation of tracking records in a custom table (`u_employee_lifecycle`) for complete auditability.
*   **Dynamic Flow Designer Logic:** Automated flow orchestrating approvals, data retrieval, and task routing.
*   **Parallel Catalog Task Creation:** Parallel dispatching of catalog tasks (`sc_task`) to IT, Facilities, and Security groups.
*   **Service Level Agreement (SLA) Tracking:** Resolution SLAs attached to catalog tasks to ensure accountability.
*   **Interactive Analytics & Dashboards:** Reports and visual gauges tracking open requests, pending approvals, and SLA statuses.

---

## 🧩 ServiceNow Implementation Details

The application leverages core ServiceNow components and custom-built objects:

*   **Custom Table:** `u_employee_lifecycle` (tracks candidate details, employee status, request type, and SLA states)
*   **Service Catalog:** Catalog items under the Human Resources category
*   **Flow Designer:** `Employee Lifecycle Orchestration Flow` triggered on request item (`sc_req_item`) creation
*   **Approval Engine:** Dynamic Routing to the employee's manager
*   **Catalog Tasks:** Generation of parallel tasks for IT, Facilities, and Security teams
*   **SLA Engine:** Standard resolution SLAs tracking time elapsed on fulfillment tasks

---

## 📐 System Architecture & Workflow

The system bridges the Service Portal UI with background fulfillment teams using a robust event-driven architecture:

```mermaid
graph TD
    %% Define styles
    classDef portal fill:#293241,stroke:#3d5a80,stroke-width:2px,color:#fff;
    classDef flow fill:#ee6c4d,stroke:#e05b38,stroke-width:2px,color:#fff;
    classDef database fill:#3d5a80,stroke:#293241,stroke-width:2px,color:#fff;
    classDef team fill:#98c1d9,stroke:#3d5a80,stroke-width:2px,color:#293241;
    classDef sla fill:#e0f2fe,stroke:#0ea5e9,stroke-width:2px,color:#0369a1;

    %% Workflow Nodes
    Portal[Service Portal Catalog Item <br/> HR Submits Request]:::portal
    
    Trigger[Flow Designer Trigger <br/> sc_req_item Created]:::flow
    GetVars[Get Catalog Variables <br/> Extract Setup Info]:::flow
    CreateRec[Create Lifecycle Record <br/> Write to u_employee_lifecycle]:::database
    MgrApprove[Manager Approval Action]:::flow
    
    BranchApproval{Is Approved?}:::flow
    
    RejectAction[Update Record to Rejected <br/> Trigger Notification]:::flow
    ApproveAction[Update Record to Approved <br/> Status: Fulfillment]:::flow
    
    ITTask[Create IT Catalog Task]:::team
    FacTask[Create Facilities Task]:::team
    SecTask[Create Security Task]:::team
    
    SlaTrack[SLA Engine Active <br/> Track Resolution SLAs]:::sla
    
    Reports[Update Reports]:::database
    EndFlow([Process Completed <br/> Status: Closed Complete]):::flow

    %% Workflow Connections
    Portal --> Trigger
    Trigger --> GetVars
    GetVars --> CreateRec
    CreateRec --> MgrApprove
    MgrApprove --> BranchApproval
    
    BranchApproval -- No --> RejectAction
    BranchApproval -- Yes --> ApproveAction
    
    ApproveAction --> ITTask
    ApproveAction --> FacTask
    ApproveAction --> SecTask
    
    ITTask & FacTask & SecTask --> SlaTrack
    SlaTrack --> Reports
    Reports --> EndFlow
```

---

## 📁 Repository Folder Structure

This repository is organized into phases and contains all project artifacts:

```text
├── README.md                          # Project overview and setup guide
├── 1.Ideation-Phase/                  # Define problem statements, brainstorming, and empathize docs
├── 2.Requirements-Analysis/           # Customer journey maps and solution requirements
├── 3.Project-Design-Phase/            # Solution architecture and proposed designs
├── 4.Project-Planning-Phase/          # Project plans and scheduling logic
├── 5.Project-Development-Phase/       # Development documentation
├── 6.Project-Documentation/           # Final project report and documents
└── Screenshots/                       # Visual proof of implementation (JPG images)
```

---

## 📸 Screenshots & Visuals

### 1. Service Portal Catalog Item View
![Service Portal View](./Screenshots/01_service_portal.jpg)

### 2. Catalog Form Layout & Client Validation
![Catalog Form](./Screenshots/02_catalog_form.jpg)

### 3. Custom Employee Lifecycle Table Record
![Employee Lifecycle Table](./Screenshots/03_employee_lifecycle_table.jpg)

### 4. Active Flow Designer Blueprint
![Flow Designer Definition](./Screenshots/04_flow_designer_definition.png.jpg)

### 5. Manager Approval Interface
![Manager Approval Request](./Screenshots/05_manager_approval_request.jpg)

### 6. Parallel Fulfillment Catalog Tasks
![Catalog Tasks Created](./Screenshots/06_catalog_tasks_created.jpg)

### 7. Task SLA Timer & Tracking
![SLA Attachment](./Screenshots/07_sla_attachment.jpg)

### 8. Analytics & Reporting
![Reports and Analytics](./Screenshots/08_reports_and_analytics.jpg)

### 9. Executive Dashboard View
![Dashboard View](./Screenshots/09_dashboard_view.jpg)

---

## 👥 Team & Roles

*   **ServiceNow Developer & Solution Architect**
    *   *Responsible for configuration, custom table creation, flow design, SLA definition, client script logic, dashboards, and reporting on the ServiceNow platform.*
