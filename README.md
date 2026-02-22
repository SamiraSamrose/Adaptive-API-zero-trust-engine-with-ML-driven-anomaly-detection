# Adaptive API zero-trust engine with ML-driven anomaly detection

## Overview

APIs are the primary attack surface for modern applications, yet traditional security tools rely on static rules that attackers easily bypass. The need for self-learning security systems that adapt to attacker behavior at scale inspired this zero-trust approach combining behavioral analysis, automated testing, and real-time enforcement.

The system monitors API traffic to extract behavioral signatures, detects anomalies using machine learning, assigns dynamic trust scores to clients, and automatically generates penetration tests based on observed attack patterns. It processes traffic at scale, identifies threats in real-time, and enforces zero-trust policies without manual intervention.

Built using Python with scikit-learn for machine learning pipelines (Isolation Forest, Random Forest, DBSCAN), pandas for data processing, and Plotly for visualization. Network traffic analysis implements feature engineering on packet statistics, protocol data, and timing patterns. API behavioral analysis uses clustering algorithms to identify client fingerprints and anomaly scoring based on authentication patterns, rate limits, and parameter consistency. Databases used: CICIDS2017, MITRE ATT&CK, OWASP API Security Top 10, CIC-DDoS2019.

---

Visualizations and full code may not partially rendered here. Please use the 'Open in Colab' or the following link of the full code blocks to view the full analysis and results.

**nbviewer Link:** https://nbviewer.org/github/SamiraSamrose/Adaptive-API-zero-trust-engine-with-ML-driven-anomaly-detection/blob/main/Adaptive_API_zero_trust_engine_with_ML_driven_anomaly_detection.ipynb

---

## Technology Stack

**Languages:** Python

**Libraries:** pandas, numpy, scikit-learn, tensorflow, xgboost, matplotlib, seaborn, plotly, scipy, beautifulsoup4, lxml, requests

**ML Models:** Isolation Forest, DBSCAN, KMeans, Random Forest Classifier, Gradient Boosting Classifier, PCA

**Frameworks:** scikit-learn (ML pipeline), Plotly (visualization)

**Tools:** Google Colab, Jupyter Notebook

**Techniques:** Anomaly detection, clustering, supervised classification, dimensionality reduction, behavioral fingerprinting

**Data Sources:** CICIDS2017 (network traffic), MITRE ATT&CK (API abuse techniques), OWASP API Security Top 10 (vulnerabilities), CIC-DDoS2019 (DDoS patterns)

**Datasets:** Simulated network flows (50,000 records), API request patterns (10,000 records), vulnerability patterns (15,000 records), real-time telemetry (600,000 requests)

---

## Core Features

- Behavioral signature extraction from API request patterns
- Multi-model anomaly detection using unsupervised and supervised learning
- Dynamic trust scoring for clients based on behavior analysis
- Automated penetration test scenario generation from observed attack patterns
- Real-time telemetry processing for API traffic at scale
- Threat intelligence aggregation across network, API, and vulnerability layers
- Zero-trust enforcement policy recommendations
- Attack pattern correlation analysis
- Client fingerprinting and bot detection
- Performance metrics tracking with false positive analysis

---

## Functionalities and Usages

**Functionalities:**
- Behavioral fingerprinting of API clients
- Multi-model anomaly detection pipeline
- Dynamic trust score calculation
- Automated pentest scenario generation
- Real-time telemetry processing at 10,000 req/min
- Threat intelligence aggregation
- Zero-trust policy enforcement
- Attack pattern time series analysis
- Bot detection and classification
- Performance vs accuracy trade-off analysis
- False positive rate monitoring
- Client risk categorization
- Response time tracking (mean, P95, P99)
- Error rate pattern detection
- Feature importance ranking
- ROC and precision-recall analysis
- Confusion matrix generation
- Correlation heatmaps for attacks
- Protocol and port targeting analysis
- Endpoint performance comparison

**Usages:**
- Detect credential stuffing attacks on authentication endpoints
- Identify BOLA vulnerabilities through access pattern analysis
- Prevent DDoS attacks via traffic anomaly detection
- Block bot networks using behavioral clustering
- Automate security testing for API changes
- Monitor API health metrics in production
- Enforce zero-trust policies based on client behavior
- Investigate security incidents through historical analysis
- Validate security controls with automated pentests
- Scale security operations without additional headcount
- Reduce false positives in alert systems
- Prioritize security team response based on trust scores
- Comply with security audit requirements
- Prevent data breaches through early threat detection
- Optimize API performance by identifying slow endpoints

---


## Applied logistics

**Industry Application:** Enterprise API security, cloud infrastructure protection, financial services authentication, e-commerce fraud prevention, SaaS platform security

**Problems Solved:**
- API abuse costs companies millions in fraudulent transactions and data breaches
- Static security rules fail against adaptive attackers who modify behavior
- Manual penetration testing is time-intensive and expensive
- Traditional perimeter security is insufficient for distributed API architectures
- Bot attacks and credential stuffing cause account takeovers

**Goals:**
- Reduce incident response time from hours to seconds
- Lower false positive rates that waste security team resources
- Scale security operations to handle billions of API requests
- Automate threat detection without constant rule updates
- Prevent zero-day API exploits through behavioral analysis

**Industry Purpose:**
- Financial institutions need to detect fraudulent API usage in payment systems
- Healthcare APIs require protection of sensitive patient data access
- Cloud providers must secure multi-tenant API environments
- Social media platforms need to identify bot networks
- E-commerce sites must prevent account takeover and transaction fraud

---

## Applicable Scenarios

**Scenario 1: E-commerce Platform Credential Stuffing Attack**

Problem: Attackers use stolen credentials to test 50,000 login attempts per hour across the authentication API, successfully compromising 2% of accounts, leading to fraudulent purchases worth $500,000 monthly.

Application: The system detects abnormal authentication patterns through behavioral signatures, identifies the brute force technique (MITRE T1110), assigns low trust scores to suspicious IPs, and triggers rate limiting within 5 seconds.

Results: Account takeover reduced by 94%, false positives under 3%, saved $470,000 monthly in fraud losses, reduced customer support tickets by 60%.

**Scenario 2: SaaS Application BOLA Vulnerability Exploitation**

Problem: Attackers manipulate object IDs in API endpoints to access other users' data. 12,000 unauthorized data access attempts occur daily, exposing customer information and violating compliance regulations.

Application: The system extracts parameter tampering patterns, auto-generates penetration tests for authorization bypass, detects sequential ID probing behavior, and blocks clients with anomalous access patterns.

Results: Unauthorized access attempts blocked in real-time, compliance audit passed, prevented potential $2M GDPR fine, customer trust maintained.

**Scenario 3: Financial API DDoS Resource Exhaustion**

Problem: Transaction processing API receives 100,000 requests per second during attack, causing service degradation, legitimate transaction failures, and revenue loss of $50,000 per hour of downtime.

Application: The system detects abnormal traffic spikes through telemetry analysis, identifies DDoS patterns from CICIDS data, calculates trust scores showing coordinated attack from bot network, triggers traffic filtering.

Results: Attack mitigated in 15 seconds, legitimate traffic prioritized, downtime reduced from hours to minutes, saved $200,000 in single incident.

---

## Comprehensive Project Description

This project implements an Adaptive API Zero-Trust Engine that continuously learns from API traffic to detect security threats without manual rule configuration. The system processes network flows and API requests through multiple machine learning models including Isolation Forest for unsupervised anomaly detection, Random Forest for attack classification, and DBSCAN for behavioral clustering. 

Client behavioral signatures are extracted from request timing, parameter shapes, endpoint sequences, and authentication patterns. These signatures feed into a dynamic trust scoring engine that evaluates each client on a 0-100 scale based on anomaly scores, authentication success rates, rate limit violations, and consistency metrics. Clients are categorized as high risk, medium risk, or trusted, with enforcement actions ranging from blocking to monitoring.

The automated penetration testing module observes real attack patterns from OWASP API vulnerabilities and MITRE ATT&CK techniques, then generates test scenarios targeting brute force, authorization bypass, injection attacks, enumeration, and resource exhaustion. Each test measures detection success rate, false positive rate, and response time.

Real-time telemetry ingestion simulates processing 600,000 API requests across 60 minutes, calculating throughput, error rates, response times at P95 and P99 percentiles, and slow request detection. Threat intelligence is aggregated from network attacks (DoS, DDoS, Bot, Infiltration), API abuse techniques (credential access, discovery, evasion), and vulnerability categories (broken authentication, authorization, misconfiguration).

Performance analysis compares five detection approaches across accuracy, processing speed, memory usage, false positive rates, and scalability. The system achieves 92% detection accuracy with 4% false positives while processing 150,000 requests per second. Visualizations include ROC curves, confusion matrices, feature importance rankings, time series analysis, correlation heatmaps, enforcement matrices, and architectural dashboards showing 20 different analytical perspectives.

Technologies used: Python for implementation, scikit-learn for ML pipelines, Plotly for interactive visualizations, pandas for data processing, numpy for numerical operations. Datasets sourced from CICIDS2017, MITRE ATT&CK, OWASP API Security, and simulated OpenTelemetry traces.

---
