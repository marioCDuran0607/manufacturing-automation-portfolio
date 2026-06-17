# Manufacturing Automation & Traceability Portfolio

Welcome to my professional engineering portfolio. This repository highlights my expertise in **Industrial Automation, Quality Assurance (Poka-Yoke), and Traceability Systems**. 

The systems documented here were designed to operate in high-volume, mission-critical manufacturing environments. They emphasize robust data architecture, real-time analytics (Digital Twin integration), and intuitive interfaces that operate reliably across the factory floor.

> **Note on Confidentiality:** The source code and documentation within this repository have been fully sanitized. Proprietary algorithms, company names, specific part numbers, and confidential network configurations have been removed or replaced with generic placeholders to protect intellectual property while still demonstrating architectural complexity.

## Core Capabilities Highlighted

1. **End-to-End Traceability:** Systems designed to log every assembly action, component validation, and operator interaction into centralized SQLite databases and real-time streams.
2. **Offline-First Resilience:** Factory networks can be unstable. These systems are built to run 100% locally on edge devices while seamlessly syncing telemetry to the cloud/server when the connection is available.
3. **Poka-Yoke Engineering:** Automated mistake-proofing systems integrating hardware sensors, computer vision, and software logic to eliminate human error during assembly.
4. **Digital Twin Integration:** Real-time data streaming architectures that feed live machine state and production metrics into centralized dashboards.

## Portfolio Components

Explore the technical documentation for my key architectural implementations:

*    **[Universal Workstation GUI Framework](./workstation-gui-framework/)**
    *   A secure, role-based graphical interface designed for edge deployment across multiple assembly stations. Features offline resilience and adaptive themes.
*    **[Digital Twin Architecture & Telemetry](./digital-twin-architecture/)**
    *   The data backbone. Explains how local stations emit real-time event streams (SSE) and manage `state.json` telemetry for immediate dashboard updates.
*    **[Torque Validation System](./torque-validation-system/)**
    *   An automated Poka-Yoke system that captures serial data from smart tools to validate and log critical fastening metrics.
*    **[Angle Detection System](./angle-detection-system/)**
    *   A computer vision-based inspection system that calculates component angles, generating permanent visual evidence (overlays) for quality audits.

## Technologies Used

- **Software:** Python, PyQt/PySide, SQLite, REST APIs, Server-Sent Events (SSE).
- **Hardware Integration:** Serial Communication (RS232/USB), Computer Vision Cameras (e.g., Keyence IV4), Edge Devices.
- **Concepts:** Digital Twin, Mistake-Proofing (Poka-Yoke), Edge Computing, Real-time Telemetry, Software Architecture.

---
*Created to showcase advanced problem-solving in manufacturing software engineering.*
