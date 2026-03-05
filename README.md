# self-healing-ai-infra
Self-healing distributed AI training platform with monitoring, alerting, and failure recovery (Colab-based)
# Self-Healing AI Infrastructure

A distributed monitoring and recovery system designed to simulate core infrastructure components used in large-scale machine learning training environments.

The system demonstrates how distributed workers can be monitored, how system anomalies can be detected from operational metrics, and how automated recovery logic can restore failed tasks.

The project uses a lightweight distributed setup to replicate essential infrastructure patterns found in modern AI training clusters.

---

## Overview

Large-scale AI training systems rely on infrastructure capable of:

* coordinating distributed compute workers
* monitoring resource utilization
* detecting system anomalies
* recovering failed tasks automatically

This project implements a simplified version of those components using Python and Ray.

Workers execute distributed workloads while system metrics are collected and analyzed to detect abnormal behavior such as CPU overload or task failures.

When failures occur, retry mechanisms simulate self-healing behavior typical of resilient distributed systems.

---

## System Architecture

The system pipeline follows a monitoring and recovery workflow:

Distributed Workers
→ Metrics Collection
→ Monitoring Pipeline
→ Anomaly Detection
→ Automated Recovery

Key stages:

1. Distributed worker processes execute tasks through the Ray framework.
2. System metrics (CPU and memory usage) are collected from running workers.
3. Metrics are stored and analyzed through a monitoring pipeline.
4. Threshold-based anomaly detection identifies abnormal resource utilization.
5. Self-healing logic retries failed jobs and measures recovery time.

---

## Core Components

### Distributed Compute Layer

Ray is used to simulate distributed workers executing compute tasks.
Each worker runs independently and produces runtime metrics that represent node-level resource utilization.

---

### Monitoring Pipeline

Worker metrics are collected during execution and stored as structured data.
The monitoring pipeline records:

* worker identifier
* process id
* CPU usage
* RAM usage
* timestamp

These metrics represent the type of telemetry collected in real training infrastructure.

---

### Anomaly Detection

A monitoring layer evaluates system metrics against predefined thresholds.

Examples:

CPU usage > 80% → CPU overload event
RAM usage > 80% → memory pressure event

Detected anomalies are logged for analysis and potential recovery actions.

---

### Self-Healing Mechanism

The system includes retry logic that simulates failure recovery.

When a task fails, the system attempts to restart the job automatically.

Recovery attempts and recovery time are recorded to evaluate system resilience.

---

## Technologies

The system is implemented using the following tools:

* Python
* Ray (distributed compute framework)
* Pandas (metrics processing)
* psutil (system telemetry)
* Google Colab runtime environment

---

## Data Outputs

The monitoring system produces several output datasets.

### Worker Metrics

Collected system metrics from distributed workers.

```
metrics/worker_metrics.csv
```

Example fields:

* worker_id
* pid
* cpu_usage
* ram_usage
* timestamp

---

### Failure Recovery Results

Records retry attempts and recovery time for simulated task failures.

```
metrics/self_healing_results.csv
```

---

### Detected Alerts

Detected anomaly events based on system monitoring thresholds.

```
metrics/alerts.csv
```

---

## Repository Str

```
self-healing-ai-infra

notebooks/
    self_healing_ai_platform.ipynb

metrics/
    worker_metrics.csv
    self_healing_results.csv
    alerts.csv

docs/
config.yaml
report.md
README.md
```

---

## Applications

This system models infrastructure patterns used in:

* distributed machine learning training pipelines
* cloud AI platforms
* large-scale compute clusters
* autonomous system training infrastructure

Monitoring, anomaly detection, and automated recovery are critical components in maintaining reliability for large distributed workloads.

---

## Coming

* GPU utilization monitoring
* Prometheus-based metrics collection
* Kubernetes cluster orchestration
* real-time monitoring dashboards
* dynamic cluster scaling

