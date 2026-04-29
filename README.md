# Cloud-Native Laboratory Information Management System (LIMS)

![Version](https://img.shields.io/badge/version-1.3.0--prototype-blue.svg)
![Tech Stack](https://img.shields.io/badge/Tech-HTML5%20%7C%20TailwindCSS%20%7C%20Vanilla%20JS%20%7C%20Chart.js-emerald.svg)
![Architecture](https://img.shields.io/badge/Architecture-Cloud--Native%20Ready-blueviolet.svg)

A high-fidelity, interactive frontend prototype designed for enterprise-level semiconductor laboratory operations. This system provides a comprehensive workflow encompassing request submission, managerial approval, WIP (Work-in-Progress) sorting, dynamic machine dispatching, and real-time capacity analytics.

## Overview

In semiconductor R&D and manufacturing, quality control relies heavily on specialized laboratories. This LIMS prototype digitizes and streamlines the lifecycle of wafer testing:
1. **Fab Users** submit detailed experimental requests.
2. **Lab Managers** evaluate machine capacity and execute approval/rejection workflows.
3. **Lab Operators** manage WIP queues and dispatch wafers to designated machines.
4. **Machine Owners** oversee equipment status, perform preventive maintenance (PM), and resolve system alarms.

## Core Architecture & Features

### 1. Secure Authentication Portal
* **Integrated Auth Flow:** Seamless Login and Registration landing pages featuring password visibility toggles and strict validation rules (e.g., minimum 8-character length, exact matching for confirmations).
* **MFA / TOTP Simulation:** Interactive 6-digit email verification step required for new account creation, complete with a 60-second anti-spam countdown timer for code resending.
* **i18n Authentication:** Fully localized (English/Traditional Chinese) portal interfaces, dynamically updating titles, buttons, and input placeholders without page reloads.

### 2. Request & Approval Workflow
* **Cross-Lab Routing:** Iterative Wafer ID input with strict Regex validation (`W-XXXX`). Supports state-persistent multi-experiment selection across different lab domains (RA, MA, FA) in a single request.
* **Managerial Review:** Real-time approval queue. Features a closed-loop rejection mechanism requiring justification, automatically syncing notifications back to the requester.

### 3. WIP Sorting & Machine Dispatching
* **1NF Data Normalization:** Approved requests are automatically parsed using Cartesian product logic, breaking down complex orders into single wafer-experiment pairs for granular WIP sorting.
* **Physical Slot Deduplication:** Dispatching logic utilizes `Set` data structures to ensure physical wafer uniqueness. Even if one wafer requires multiple experiments, it strictly occupies only one physical capacity slot in the target machine.
* **Cascading Configurations:** Dynamic linkage between Target Machine and Recipe selections based on real-time equipment availability.

### 4. FSM-Based Machine Management
* **Finite State Machine (FSM):** Strict state transition logic handling `IDLE`, `PROCESSING`, `ALARM`, and `MAINTENANCE` states.
* **State Memory Preservation:** Simulating real-world scenarios, machines entering `ALARM` or `MAINTENANCE` mode safely preserve their internal loaded wafers, automatically resuming `PROCESSING` status once resolved.
* **Preventive Maintenance (PM):** Dedicated maintenance toggles to securely lock machines out of the dispatching queue during PM cycles.

### 5. Advanced Capacity Analytics
* **Time-Series Visualization:** Integration with Chart.js to render dynamically calculated utilization metrics based on real-time loaded capacity.
* **Segmented Dashboards:** Equipment data is intelligently split into "Analysis" (SEM, TEM, FIB) and "Process & Test" (BAKE, E-TEST, XRD) for optimized readability.
* **Dynamic Time Ranges:** Granular utilization tracking supporting views from the last 5 minutes up to the past week.

### 6. Enterprise UI & Security Control
* **Role-Based Access Control (RBAC):** UI dynamically adapts to primary roles (System Admin, Lab Supervisor, Lab Operator, Machine Owner, Fab User), strictly restricting navigation and management models.
* **Responsive Design:** Mobile-first architecture featuring collapsible sidebars and off-canvas layouts for cross-device accessibility.
* **Data Sanitization:** SAP-standard automated formatting for user profile contact fields.

## Technology Stack

* **Frontend Framework:** HTML5, Tailwind CSS
* **Data Visualization:** Chart.js
* **Logic & State:** Vanilla JavaScript (ES6+)
* **Icons & Typography:** Google Material Symbols, Public Sans

## Getting Started

This is a pure frontend architecture designed with zero-build-step principles. No external dependencies or package managers are required.

1. Clone the repository:
   ```bash
   git clone [https://github.com/jasper-nycu/LIMS.git](https://github.com/jasper-nycu/LIMS.git)