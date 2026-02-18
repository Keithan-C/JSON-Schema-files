# LXD Compliance Schemas

This directory contains the core technical definitions required to automate **EU AI Act** compliance. By using standardized JSON schemas, we transform regulatory requirements into machine-readable system requirements.

## Current Schemas

### 1. Article 12: Automated Logging (`article-12-v1.json`)
This schema defines the telemetry required for high-risk AI systems to ensure traceability throughout their lifecycle.
* **Key Focus:** Capturing the "Reasoning Logic" and "Confidence Scores" at the moment of inference.
* **Audit Value:** Provides the "Black Box" evidence required for ASIL D (ISO 26262) and AI Act transparency.

### 2. Article 11: Technical Documentation (Coming Soon)
A metadata schema designed to automate the export of technical files directly from your CI/CD pipeline.

## Technical Implementation
These schemas are designed to be **language-agnostic**. Whether your system is built in Python (Procurement/CAE) or C++ (ADAS/Middleware), you can use these definitions to:
1. **Validate Data:** Ensure your logs meet the minimum regulatory threshold.
2. **Standardize Output:** Create a unified "Audit Defense" stream across different departments (OEM, Tier-1, Tier-2).

## Why JSON Schema?
* **Machine Readable:** Enables automated compliance testing.
* **Zero Overhead:** Can be implemented as an "Interceptor" pattern that does not interfere with core AI performance.
* **Future-Proof:** Easily extensible as the EU Commission releases further "Implementing Acts."
