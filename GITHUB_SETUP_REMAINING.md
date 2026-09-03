# GitHub Portfolio — Remaining UI-Only Setup

The repository content has been prepared. The current ChatGPT GitHub connector can edit existing repositories but does not expose repository creation, repository renaming, profile-bio editing, topic editing, or pinning actions.

Complete the following GitHub UI actions to finish the portfolio structure.

## 1. Create the special profile repository

Create a new **public** repository with this exact name:

```text
Shahabrjb
```

GitHub treats a public repository whose name exactly matches the username as the profile README repository.

Copy the current `About-Me/README.md` into `Shahabrjb/README.md`.

After this is done, the full research profile will appear directly at:

```text
https://github.com/Shahabrjb
```

## 2. Create a standalone RF showcase repository

Recommended repository name:

```text
rf-optimization-platform
```

Make it public, but **do not upload the production software package**.

Move/copy the following prepared public files from `About-Me`:

```text
projects/rf-optimization-platform/README.md
projects/rf-optimization-platform/ARCHITECTURE.md
```

Recommended description:

```text
AI-assisted multi-module RAN optimization platform — public architecture and research showcase.
```

## 3. Create the ongoing research repository

Recommended repository name:

```text
adaptive-ran-anomaly-detection
```

Copy these prepared files:

```text
projects/adaptive-ran-anomaly-detection/README.md
projects/adaptive-ran-anomaly-detection/METHODOLOGY.md
```

Recommended description:

```text
Adaptive Isolation Forest research for impact-aware prioritization of unbalanced RAN sectors using temporal ML.
```

Keep detailed unpublished implementation and operator data private until the research is ready for publication.

## 4. Update profile bio

Recommended bio:

```text
Machine Learning & RAN Optimization Engineer | AI for Wireless Networks | Anomaly Detection | Time-Series Learning
```

## 5. Pin repositories

Recommended order:

1. `rf-optimization-platform`
2. `adaptive-ran-anomaly-detection`
3. `MLP-based-Learnable-Window-Size-for-Bitcoin-Price-Prediction`
4. `adaptive-time-series-forecasting`
5. `Persian-sign-language-detection-based-on-normalized-depth-image-information`

## Confidentiality rule

Never publish:

- operator KPI/raw performance files
- real site/cell identifiers
- network-element backups
- credentials or keys
- proprietary vendor documentation
- full production RF Optimization Platform source
- unpublished experiment data/results that should remain protected before paper submission
