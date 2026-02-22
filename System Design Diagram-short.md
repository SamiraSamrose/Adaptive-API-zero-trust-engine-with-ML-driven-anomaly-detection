## Architecture Diagram

```
                    ADAPTIVE API ZERO-TRUST ENGINE (A-ZTE)
                                                                        
    ┌──────────────────────────────────────────────────────────────────┐
    │                       DATA SOURCES                               │
    │  [CICIDS2017] [MITRE ATT&CK] [OWASP API] [Telemetry Stream]      │
    └────────────────────────────┬─────────────────────────────────────┘
                                 │
                                 ▼
    ┌──────────────────────────────────────────────────────────────────┐
    │              FEATURE EXTRACTION & PREPROCESSING                  │
    │  Behavioral Signatures | Timing Patterns | Parameter Analysis    │
    └────────────────────────────┬─────────────────────────────────────┘
                                 │
                                 ▼
    ┌──────────────────────────────────────────────────────────────────┐
    │                   ML DETECTION MODELS                            │
    │  [Isolation Forest] [DBSCAN Clustering] [Random Forest]          │
    └────────────────────────────┬─────────────────────────────────────┘
                                 │
                                 ▼
    ┌──────────────────────────────────────────────────────────────────┐
    │              ZERO-TRUST SCORING ENGINE                           │
    │  Calculate Trust Score (0-100) → Categorize Risk Level           │
    └────────────────────────────┬─────────────────────────────────────┘
                                 │
                ┌────────────────┼────────────────┐
                │                │                │
                ▼                ▼                ▼
    ┌──────────────────┐ ┌──────────────┐ ┌─────────────────┐
    │   AUTOMATED      │ │   THREAT     │ │  ENFORCEMENT    │
    │   PENTEST        │ │ INTELLIGENCE │ │    ACTIONS      │
    │   GENERATOR      │ │ AGGREGATION  │ │                 │
    └──────────────────┘ └──────────────┘ └─────────────────┘
                │                │                │
                └────────────────┼────────────────┘
                                 │
                                 ▼
                    ┌────────────────────────┐
                    │   ANALYTICS & OUTPUT   │
                    │  Dashboards | Metrics  │
                    └────────────────────────┘
```

---