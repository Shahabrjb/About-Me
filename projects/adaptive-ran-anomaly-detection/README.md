# Adaptive RAN Anomaly Detection for High-Impact Unbalancing Optimization

**Ongoing Research**

This project investigates how anomaly detection can be used not only to identify unusual or traffic-unbalanced cellular sectors, but to prioritize the sectors whose optimization is expected to produce the **largest improvement in downlink spectral efficiency**.

## Research Problem

A conventional anomaly-detection pipeline can identify sectors whose KPI behaviour differs from the broader network population. However, operationally, the most anomalous sector is not always the most valuable one to fix.

The research therefore focuses on two linked questions:

1. **Which sectors are genuinely anomalous or unbalanced?**
2. **Which of those anomalies are expected to deliver the highest engineering benefit if corrected?**

The target outcome is an **impact-aware ranking**, rather than a simple binary anomaly label.

## Current Methodology

### 1. Network KPI Preparation

Historical and cross-sectional RAN KPIs are transformed into a feature set representing traffic distribution, throughput, radio quality, utilization, and other engineering indicators relevant to sector imbalance.

### 2. Isolation Forest Screening

Isolation Forest is used as the primary unsupervised anomaly detector.

Instead of assuming a single fixed contamination rate for all network conditions, the research investigates an **adaptive contamination-rate selection strategy**.

### 3. LSTM-Based Contamination-Rate Estimation

An LSTM-based model is being explored to estimate the most appropriate Isolation Forest contamination rate from **temporal KPI behaviour**.

The central hypothesis is that the expected proportion and structure of anomalies can change with network conditions, traffic evolution, seasonality, and distribution shift; therefore, a fixed contamination setting may not be optimal across all periods.

### 4. Impact-Aware Prioritization

Detected anomaly candidates are ranked using evidence related to their expected influence on **spectral efficiency**.

The research goal is to prioritize anomalies according to likely optimization value:

```text
Historical RAN KPIs
        |
Temporal feature sequences
        |
LSTM-based contamination estimation
        |
Isolation Forest anomaly detection
        |
Candidate unbalanced sectors
        |
Spectral-efficiency impact evaluation
        |
High-impact optimization priority ranking
```

## Key Research Question

The phrase **"best contamination rate"** must be defined by an explicit objective rather than selected heuristically.

The planned evaluation therefore compares candidate contamination rates according to how well the resulting anomaly set and ranking correspond to downstream engineering impact, especially spectral-efficiency improvement opportunity.

Possible evaluation components include:

- ranking quality
- stability across time windows
- consistency with engineering validation
- separation of high-impact versus low-impact candidates
- comparison with fixed-contamination Isolation Forest baselines

## Why LSTM?

LSTM is used only where the input contains meaningful temporal structure. The motivation is to learn how changes in KPI sequences and network conditions relate to the appropriate anomaly proportion for a given period.

This is important methodologically: if the input were only a static network snapshot, a non-sequential model such as gradient boosting or an MLP would be a more natural baseline. The study therefore includes comparison against simpler alternatives where appropriate.

## Planned Baselines

- Isolation Forest with fixed contamination values
- Isolation Forest with contamination selected by grid search / validation objective
- non-sequential predictor for contamination-rate selection
- LSTM-assisted adaptive Isolation Forest

## Intended Contribution

The intended novelty is the combination of:

- unsupervised anomaly detection for network imbalance
- temporal prediction of an Isolation Forest hyperparameter
- engineering-impact-aware anomaly ranking
- direct linkage between anomaly prioritization and spectral-efficiency optimization

The broader objective is to move from **"find abnormal cells"** to **"find the abnormal cells worth fixing first."**

## Publication Status

This work is currently under development. Detailed experimental implementation, operator data, and unpublished results are intentionally not released publicly before the research is ready for publication.

## Research Context

This project is connected to my broader work on adaptive machine learning, time-series modelling, and AI-assisted RAN optimization.

- [RF Optimization Platform](../rf-optimization-platform/README.md)
- [Portfolio](../../README.md)

## Author

**Shahab Rajabi**  
Machine Learning & RAN Optimization Engineer
