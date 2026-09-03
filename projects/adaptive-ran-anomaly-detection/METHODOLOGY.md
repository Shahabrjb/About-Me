# Methodology and Evaluation Plan

This note defines the public research design at a level that is useful for academic discussion while intentionally excluding operator data and unpublished experimental results.

## 1. Problem Definition

Let each network sector be represented by a set of engineering and performance indicators collected over time. The task is to identify sectors that are both:

1. anomalous with respect to network behaviour, and
2. operationally important because correcting their traffic imbalance is expected to improve downlink spectral efficiency.

The desired output is therefore a **ranked optimization-priority list**, not only an anomaly label.

## 2. Feature Families

Candidate feature groups include:

- traffic distribution and imbalance indicators
- downlink throughput
- spectral efficiency
- PRB / resource utilization
- radio-quality indicators
- temporal change / trend features
- sector-relative and peer-relative features

Exact operator-specific KPI names are excluded from the public research note.

## 3. Isolation Forest

Isolation Forest provides the primary unsupervised anomaly score. A key hyperparameter is the contamination rate, which influences the expected proportion of observations labelled as anomalous.

A fixed contamination rate may be too restrictive when the network distribution evolves over time.

## 4. Adaptive Contamination Selection

The proposed adaptive workflow estimates a contamination rate for each analysis period from temporal KPI behaviour.

Candidate approach:

```text
KPI sequence over historical periods
              |
        temporal encoder
              |
     predicted contamination
              |
       Isolation Forest
              |
       anomaly candidates
```

LSTM is the main temporal model under investigation. Simpler non-sequential methods should be included as baselines to demonstrate whether temporal modelling contributes measurable value.

## 5. Defining the Target

A major methodological requirement is to avoid defining the "best" contamination rate by intuition alone.

For each training/validation period, candidate contamination values can be evaluated over a predefined range. Each candidate produces an anomaly set and ranking. The preferred contamination value is then selected according to an objective that reflects downstream engineering usefulness.

The exact objective is part of the experimental design and may combine:

- separation of high-impact versus low-impact sectors
- ranking quality
- engineering validation
- temporal stability
- relationship with subsequent spectral-efficiency improvement opportunity

## 6. Impact Ranking

An anomaly score alone does not determine optimization priority. A second stage estimates or measures expected impact on spectral efficiency so that high-impact sectors move to the top of the list.

Conceptually:

```text
Priority = f(anomaly evidence, imbalance severity, expected SE impact, engineering validity)
```

The final formulation will be selected through experiment and validation rather than fixed in this public note.

## 7. Baselines

The research should compare the adaptive method with at least:

- fixed contamination Isolation Forest
- multiple fixed contamination values
- validation-selected contamination without temporal prediction
- non-sequential contamination predictor
- LSTM-based contamination predictor

## 8. Evaluation

Evaluation should address both anomaly quality and operational usefulness.

### Detection / ranking evaluation

- ranking consistency
- top-k quality
- stability across time
- sensitivity to contamination changes

### Engineering evaluation

- concentration of validated unbalancing cases in the top-ranked set
- relation between priority rank and expected spectral-efficiency benefit
- comparison of optimization yield under fixed versus adaptive contamination

## 9. Leakage and Validation

Because network KPI data is temporal, train/validation/test splits should preserve time order whenever future information could leak into earlier decisions.

Normalization, feature construction, and target generation must be performed in a way that avoids using future-period information during training.

## 10. Research Claim Discipline

The public project intentionally distinguishes:

- **implemented / validated findings**
- **methods currently under investigation**
- **planned baselines and evaluation**

No performance claim should be made until the corresponding experiment has been completed and documented.
