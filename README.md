# Cloud-Native Laboratory Information Management System (LIMS) ??

![Version](https://img.shields.io/badge/version-1.0.0--prototype-blue.svg)
![Tech Stack](https://img.shields.io/badge/Tech-HTML5%20%7C%20TailwindCSS%20%7C%20Vanilla%20JS-emerald.svg)
![Architecture](https://img.shields.io/badge/Architecture-Cloud--Native%20Ready-blueviolet.svg)

A high-fidelity, interactive frontend prototype for a Cloud-Native Laboratory Information Management System. This project is meticulously designed to align with enterprise-level semiconductor lab operations, providing seamless workflows from request submission to machine dispatching.

## ?? Executive Summary

In semiconductor R&D and manufacturing, quality control relies heavily on specialized laboratories. This LIMS prototype streamlines the entire lifecycle of wafer testing:
1. **Fab Users** submit detailed experiment requests.
2. **Lab Managers** perform capacity checks and approve requests.
3. **Lab Operators** manage WIP (Work-in-Progress) sorting and dispatch wafers to specific testing machines.

## ? Core Features

### 1. End-to-End Workflow Integration
* **Fab Request (Order Creation):** Iterative Wafer ID input with strictly enforced regex validation (`W-XXXX`). Supports multi-select experiments and priority assignment.
* **Manager Dashboard (Approval Queue):** Real-time approval workflow. Includes order remarks parsing, capacity evaluation, and dynamic pending counters.
* **Lab Operations (WIP & Dispatch):** Closed-loop data flow. Approved requests are automatically deconstructed into individual wafers and queued in the WIP sorting area. Features a "Select All" mechanism and direct machine dispatching.

### 2. Machine Management & FSM (Finite State Machine)
* Real-time machine status monitoring (`PROCESSING`, `IDLE`, `ALARM`).
* Dynamic machine ownership assignment based on Role-Based Access Control (RBAC).
* Built-in incident response (e.g., resolving vacuum loss alarms) and history logging.

### 3. Advanced Analytics & Gantt Charts
* Visualized weekly Machine Idle Time utilizing interactive Gantt chart logic.
* Automatically calculated Average Utilization metrics across various tool groups (SEM, BAKE, TEM, FIB, E-TEST, XRD).

### 4. Enterprise-Grade UX/UI
* **Responsive Web Design (RWD):** Mobile-first approach with an off-canvas sidebar, smart grid stacking, and scrollable data tables for on-the-go accessibility.
* **i18n Localization:** Instant switching between English (EN) and Traditional Chinese (TW) without page reloads.
* **Notification Center:** Dynamic alert system with unread counters and interactive dismissals.

## ??? Technology Stack

* **Frontend:** HTML5, Tailwind CSS (via CDN for rapid prototyping)
* **Scripting:** Vanilla JavaScript (ES6+)
* **Icons & Typography:** Google Material Symbols, Public Sans Font
* **Deployment:** GitHub Pages (Zero-build-step architecture)

## ?? Getting Started

Since this is a pure frontend prototype, no complex build tools or dependencies are required.

1. Clone the repository:
   ```bash
   git clone [https://github.com/jasper-nycu/LIMS.git](https://github.com/jasper-nycu/LIMS.git)