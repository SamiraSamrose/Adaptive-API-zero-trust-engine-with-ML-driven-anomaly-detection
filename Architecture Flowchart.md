## Architecture Flowchart

```
                              START
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Load Datasets        │
                    │  - CICIDS2017         │
                    │  - MITRE ATT&CK       │
                    │  - OWASP API          │
                    │  - Telemetry Stream   │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Data Preprocessing   │
                    │  - Normalize values   │
                    │  - Encode labels      │
                    │  - Scale features     │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Extract Behavioral   │
                    │  Signatures           │
                    │  - Request timing     │
                    │  - Parameter shapes   │
                    │  - Auth patterns      │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Generate Client      │
                    │  Fingerprints         │
                    │  - 1000 unique clients│
                    └───────────┬───────────┘
                                │
                ┌───────────────┼───────────────┐
                │               │               │
                ▼               ▼               ▼
    ┌──────────────────┐ ┌─────────────┐ ┌──────────────┐
    │ Isolation Forest │ │   DBSCAN    │ │Random Forest │
    │  Train Model     │ │  Clustering │ │  Train/Test  │
    │  Predict Anomaly │ │  Find Groups│ │  Classify    │
    └────────┬─────────┘ └──────┬──────┘ └──────┬───────┘
             │                  │               │
             └──────────────────┼───────────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Aggregate Predictions│
                    │  - Anomaly scores     │
                    │  - Cluster labels     │
                    │  - Classification     │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Calculate Trust Score│
                    │  for each client      │
                    │                       │
                    │  Formula:             │
                    │  Base 100             │
                    │  - Anomaly penalty    │
                    │  - Auth failure       │
                    │  - Rate limit         │
                    │  - Inconsistency      │
                    │  - Bot detection      │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Categorize Clients   │
                    │  0-40:   High Risk    │
                    │  40-70:  Medium Risk  │
                    │  70-100: Trusted      │
                    └───────────┬───────────┘
                                │
                ┌───────────────┼───────────────┐
                │               │               │
                ▼               ▼               ▼
    ┌──────────────────┐ ┌─────────────┐ ┌──────────────┐
    │Generate Pentest  │ │  Aggregate  │ │  Determine   │
    │Scenarios from    │ │  Threat     │ │  Enforcement │
    │Attack Patterns   │ │  Intel      │ │  Policy      │
    │- Brute force     │ │  - Network  │ │  - Block     │
    │- BOLA            │ │  - API      │ │  - Challenge │
    │- DoS/DDoS        │ │  - Vuln     │ │  - Monitor   │
    │- Injection       │ │             │ │  - Allow     │
    │- Enumeration     │ │             │ │              │
    └────────┬─────────┘ └──────┬──────┘ └──────┬───────┘
             │                  │               │
             └──────────────────┼───────────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Process Telemetry    │
                    │  - Aggregate 5min     │
                    │  - Calculate metrics  │
                    │  - Error rates        │
                    │  - Response times     │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Performance Analysis │
                    │  - ROC/AUC curves     │
                    │  - Confusion matrix   │
                    │  - Feature importance │
                    │  - Model comparison   │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Generate             │
                    │  Visualizations       │
                    │  - 20 chart types     │
                    │  - 8 dashboards       │
                    │  - Performance graphs │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Output Results       │
                    │  - Summary report     │
                    │  - Metrics            │
                    │  - Recommendations    │
                    └───────────┬───────────┘
                                │
                                ▼
                              END
```