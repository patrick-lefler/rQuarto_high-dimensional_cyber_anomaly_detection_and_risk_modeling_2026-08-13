### High-Dimensional Cyber Anomaly Detection & Systemic Risk Modeling

Integrating Markov Transition Matrices, Deep Autoencoder Reconstruction Loss, and Extreme Value Theory Tail Calibration

Author: Patrick Lefler 

Published: 2026-08-12 

GitHub Link: https://patrick-lefler.github.io/rQuarto_high-dimensional_cyber_anomaly_detection_and_risk_modeling_2026-08-13/

### Project Introduction

A pure-R detection engine pairs PageRank structural-risk mapping with an unsupervised autoencoder and Extreme Value Theory thresholds for board-grade cyber monitoring.

### Overview

The project layers two independent risk models on enterprise telemetry. A Markov transition matrix maps how requests and dependencies move across services, and a PageRank pass over that graph identifies the single points of failure most likely to produce cascading outages. Separately, an unsupervised autoencoder — built from vectorized matrix calculus and trained with the Adam optimizer, with no external C++ or LibTorch dependency — learns the reconstruction signature of sixteen telemetry features and flags deviation through reconstruction error. Extreme Value Theory, via a Peaks-over-Threshold fit of a Generalized Pareto Distribution to the loss tail, replaces a fixed alert rule with a statistically derived 99.9% boundary. The intended outcome is a monitoring layer decision-makers can trust to isolate real threats without burying the SOC in false positives.

### Tech Stack
Language: R
Framework: Quarto, tidymodels (recipes, parsnip, workflows, tune, rsample, yardstick) for the evaluation pipeline
Primary Libraries: tidyverse, evd (Generalized Pareto / EVT fitting), gt, patchwork, scales, sessioninfo
Deployment/Output: Self-contained HTML report (embed-resources: true)
Repository Structure
high-dimensional-cyber-anomaly-detection/
├── data/               # Simulated baseline telemetry and injected attack vectors
├── scripts/            # Autoencoder engine, EVT calibration, and graph-analysis helpers
├── models/             # Saved autoencoder weights and simulation draws (.rds)
├── output/              # Rendered HTML report
├── _brand.yml
├── _quarto.yml
└── index.qmd
### Key Findings

Reflects performance against simulated telemetry and controlled attack injection, not live production traffic.

The autoencoder-plus-EVT engine reached a perfect AUC-ROC (1.0000) against 450 injected attacks: 100.0% detection of credential stuffing and zero-day lateral movement, 96.7% of data exfiltration, at the strict 99.9% EVT threshold, with zero false alarms across 5,000 baseline observations.
Extreme Value Theory thresholding outperforms a fixed cutoff on its own terms — tightening from a 99.0% to a 99.9% confidence boundary cut SOC false alarms from 37 to zero without losing detection coverage.
Feature-level error decomposition attributes every flagged incident to specific telemetry drivers (failed-login and source-IP spikes for credential stuffing; outbound transfer volume and TLS duration for data exfiltration; DNS query and child-process activity for zero-day lateral movement), giving the auditable root-cause trail that NIST AI RMF and OSFI E-23 expect.
License

This project is licensed under the MIT License. See the LICENSE file for details.

### Contact

Patrick Lefler [https://www.linkedin.com/in/patricklefler/] | [patrick-lefler.github.io] | [https://substack.com/@pflefler]

See task progress for longer tasks.

README.md
Abstract.md
README-High_Dimensional_Cyber_Anomaly_Detection.md
Abstract-High_Dimensional_Cyber_Anomaly_Detection.md
rQuarto_projects
