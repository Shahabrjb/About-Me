# RF Optimization Platform

**AI-Assisted Multi-Module RAN Optimization and Decision-Support Software**

This project is a production-oriented Python desktop platform developed to support large-scale radio access network (RAN) optimization workflows. It combines **performance KPIs, configuration data, inventory information, RF engineering rules, anomaly detection, root-cause analysis, and optimization recommendations** in a single engineering environment.

The complete production source code and real operator datasets are intentionally **not public**. This repository page documents the platform at an architectural and research level only.

## Why I Built It

RAN optimization work often requires engineers to move between large KPI exports, configuration backups, inventory files, drive-test logs, vendor-specific parameters, and manually maintained rule sets. The platform was designed to reduce that fragmentation by turning multiple engineering inputs into a structured analytical workflow:

**Import data → validate and normalize → correlate evidence → detect problems/opportunities → rank impact → generate RCA and recommendations → export engineering reports**

## Main Capabilities

### Traffic Unbalancing

- Detects traffic imbalance across sectors/cells
- Combines performance and engineering evidence
- Supports anomaly-based prioritization
- Ranks sectors by expected optimization value rather than imbalance magnitude alone

### MIMO / eMIMO Analysis

- Correlates MIMO KPIs with radio configuration
- Evaluates high-rank opportunity versus actual usage
- Checks configuration consistency and capability constraints
- Produces concise root-cause categories and recommended actions

### Carrier Aggregation

- Validates CA configuration and performance evidence
- Checks component-carrier readiness and same-site relation logic
- Distinguishes not-analyzed, blocked, misconfigured, and optimization-opportunity cases

### Power Analysis

- Evaluates configured versus effective radio power
- Uses RRU and cell configuration evidence
- Identifies under-utilized or constrained power configurations

### BBP Capacity

- Evaluates baseband-board capacity against configured LTE/UMTS/NR load
- Supports board-model-specific engineering rules
- Correlates configuration and licensing evidence

### Modernization Planning

- Prioritizes sectors for modernization using traffic, throughput, bandwidth, and prerequisite checks
- Uses evidence from other analytical modules before proposing upgrade actions

### NE Backup Analysis

- Parses Huawei network-element configuration backups
- Extracts managed objects into structured datasets
- Makes configuration evidence reusable across analytical modules

### Fault Detection and Configuration Validation

- Detects configuration mismatches and potential sector/RF faults
- Combines configuration evidence with operational performance indicators

### Drive-Test Analysis

- Imports drive-test measurement sources
- Provides route-based RF visualization and engineering inspection workflows
- Supports event-oriented analysis and RF root-cause workflows

### AI / ML Intelligence

- Isolation Forest-based anomaly detection for high-dimensional network data
- Time-series and predictive modelling workflows
- Research work on adaptive model configuration and impact-aware anomaly ranking

## Engineering Architecture

The software is organized around independent analytical pipelines connected to a shared data-import and normalization layer.

```text
Network KPIs          Configuration / NE Backup       Inventory / RF Data
     |                          |                           |
     +--------------------------+---------------------------+
                                |
                     Data ingestion & normalization
                                |
                     Cross-source evidence mapping
                                |
      +-------------------------+--------------------------+
      |             |             |            |           |
 Unbalancing       MIMO           CA          Power       BBP / DT / ...
      |             |             |            |           |
      +-------------------------+--------------------------+
                                |
                RCA + impact scoring + recommendations
                                |
                     Dashboard and report generation
```

## Multi-Vendor Direction

The platform includes vendor-aware parsing and knowledge components for **Huawei, Ericsson, and Nokia** data sources. Different modules currently have different levels of vendor coverage depending on the availability and structure of configuration evidence.

## Software Engineering Scope

The full package contains hundreds of source, test, validation, and release-support files. Development has included:

- modular Python architecture
- automated regression tests
- large-file and archive import workflows
- configuration-schema handling
- desktop dashboard development
- Excel/report generation
- rule-based engineering validation
- ML integration
- Windows packaging/build workflows

## Research Connection

The platform also acts as an applied research environment for testing ML methods on real engineering problems. One current research direction is **adaptive anomaly detection for traffic-unbalanced sectors**, where Isolation Forest is combined with temporal modelling to identify the sectors whose correction is expected to produce the greatest spectral-efficiency benefit.

[Read the ongoing anomaly-detection research overview](../adaptive-ran-anomaly-detection/README.md)

## Confidentiality and Public Scope

This public showcase deliberately excludes:

- complete production source code
- operator/customer datasets
- real network identifiers
- configuration backups
- proprietary vendor documentation
- credentials, secrets, or internal deployment information

Public material is limited to architecture, methodology, sanitized screenshots, non-sensitive descriptions, and research concepts.

## Author

**Shahab Rajabi**  
Machine Learning & RAN Optimization Engineer  
Research interests: AI for wireless networks, anomaly detection, adaptive ML, time-series learning, and intelligent RAN optimization.

[Back to portfolio](../../README.md)
