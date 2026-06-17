# Computer Vision Angle Detection System

This directory covers the implementation details of an automated visual inspection system designed to verify geometric tolerances (specifically bending angles) on manufactured assemblies.

## Overview

Traditional manual angle measurement using protractors or gauges is slow, subjective, and highly dependent on operator skill. This system automates the process using a high-definition vision sensor (e.g., Keyence IV4) combined with edge-computing software. It calculates the angle formed by bent components and cross-references it against strict engineering tolerances.

## System Architecture

### 1. Vision Hardware Integration
The system communicates seamlessly with industrial smart cameras over a local network.
- **Triggering:** The software automatically triggers the camera to capture an image once a sensor detects the part is correctly seated in the inspection fixture.
- **Image Processing:** The camera captures the image and identifies two intersecting lines along the edges of the part to compute the exact internal/external angle.

### 2. Software Validation Logic
The Python-based backend receives the raw data from the camera.
- **Tolerance Checking:** The software compares the measured angle (e.g., 89.5°) against the acceptable upper and lower bounds for that specific part number (e.g., 90° ± 1°).
- **Automated Decision:** It outputs an immediate Pass/Fail result to the operator GUI, physically preventing the part from advancing if the bend is out of specification.

### 3. Traceability & Visual Evidence (Overlays)
Unlike simple Go/No-Go systems, this implementation provides deep traceability.
- **Permanent Visual Record:** For every inspection, the system downloads the raw image from the camera.
- **Overlay Generation:** The software draws visual overlays (green lines for "Pass", red lines for "Fail") directly on the image, denoting the exact edges detected and the angle calculated.
- **Data Archiving:** These annotated images are saved to a specific `images/overlay/` directory, named with the timestamp and unique serial number.
- **Auditing:** Quality Engineers can review the visual evidence of any past failure remotely via the Digital Twin dashboard, without needing to retrieve the physical part.

## Technical Stack
- **Language:** Python
- **Vision Hardware:** Keyence IV4 (or similar industrial vision sensors)
- **Networking:** TCP/IP communication for triggering and image retrieval.
- **Data Logging:** SQLite for metadata and OS file-system for image storage.
