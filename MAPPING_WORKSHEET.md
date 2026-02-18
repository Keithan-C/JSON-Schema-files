# LXD Advisory: AI Act Article 12 Mapping Worksheet

## Overview
This worksheet is the core of the **Artifact-as-Code** integration. During the 3-week pilot, we map your internal system variables to the standardized **LXD Article 12 Schema**. 

**Goal:** Ensure every AI inference generates a compliant, audit-ready log without impacting system performance.

---

## 1. Technical Variable Mapping
*Lead Developers: Please identify the internal variables or telemetry points that correspond to the compliance fields below.*

| LXD Schema Field (Standard) | Internal System Variable (Source) | Format | Description |
| :--- | :--- | :--- | :--- |
| `model_version` | | string | The unique ID/Hash of the model in production. |
| `timestamp` | | ISO-8601 | Server/UTC time of the inference event. |
| `input_data_integrity` | | boolean | Did the input pass quality/pre-processing checks? |
| `confidence_threshold` | | float | The pre-defined 'Go/No-Go' bar (e.g., 0.85). |
| `actual_confidence` | | float | The model's raw probability output for the decision. |
| `decision_logic_id` | | string | Identifier for the logic branch or rule triggered. |
| `human_intervention` | | boolean | Was a manual override or takeover detected? |
| `system_health` | | enum | Current status of sensors/infrastructure (e.g., Nominal). |

---

## 2. Integration Checklist
- [ ] **Data Sink Identified:** Where will these JSON logs be stored? (e.g., AWS S3, Azure Blob, Local SSD).
- [ ] **Frequency Defined:** Is the system logging *every* decision, or a statistically significant sample?
- [ ] **Security:** Is the metadata stripped of PII (Personally Identifiable Information)?
- [ ] **Retention:** Is the storage configured for the required EU retention period?

---

## 3. Implementation Example (Python/Pseudo-code)
```python
# During the 2-hour session, we will implement a wrapper similar to this:

compliance_artifact = {
    "metadata": {
        "model_version": YOUR_INTERNAL_VAR_HERE,
        "timestamp": get_timestamp()
    },
    "inference_logic": {
        "actual_confidence_score": YOUR_INTERNAL_VAR_HERE,
        "decision_path": YOUR_INTERNAL_VAR_HERE
    }
}

# The goal is 'Compliance-as-Telemetry'
lxd_compliance_logger.emit(compliance_artifact)
