

<h1 align="center">Scarlet Moore</h1>
<p align="center"><strong>Operations Engineer</strong> · <strong>Technical Product Strategy</strong> · <strong>MBA Candidate</strong></p>

<p align="center"><em>Building auditable, reproducible operational tooling and telemetry pipelines for regulated environments. I design systems that make data trustworthy, observable, and cost‑ and carbon‑aware.</em></p>

<hr />

## Summary

**Focus areas:** telemetry engineering, reproducible data pipelines, secure signing & audit trails, ML infrastructure, offline‑first PWAs, and governance tooling.  
**Approach:** small, testable components; observable defaults; defense‑in‑depth for integrity and compliance; measurable product outcomes.

---

## Core Projects (quick map)

<table>
  <thead>
    <tr>
      <th align="left">Project</th>
      <th align="left">Stack</th>
      <th align="left">Technical scope</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>carbon-ops</strong></td>
      <td>Python · Vertex AI</td>
      <td>Telemetry ingestion → CO₂e estimation; ed25519 signing; Merkle anchoring for tamper-evident logs</td>
    </tr>
    <tr>
      <td><strong>vertex-batch-api</strong></td>
      <td>GCP · Docker</td>
      <td>Batch orchestration for Vertex AI; GCS streaming; idempotent retries; error classification</td>
    </tr>
    <tr>
      <td><strong>acs-energy-toolkit</strong></td>
      <td>Python · Pandas</td>
      <td>Time-series energy analysis; uncertainty quantification; reproducible notebooks & CI data checks</td>
    </tr>
    <tr>
      <td><strong>chimera</strong></td>
      <td>Node.js · GraphQL</td>
      <td>High-throughput artifact processing; consent-aware API gateway; backpressure & rate limiting</td>
    </tr>
    <tr>
      <td><strong>kensho</strong></td>
      <td>React · PWA</td>
      <td>Offline-first sync; IndexedDB conflict resolution; encrypted voice capture</td>
    </tr>
    <tr>
      <td><strong>devtools</strong></td>
      <td>GitHub Actions · CLI</td>
      <td>Repo governance automation; pre-commit hooks; secret scanning; changelog enforcement</td>
    </tr>
  </tbody>
</table>

---

## Technical highlights & patterns

### Observability
- Structured JSON telemetry with schema validation and sampling controls.  
- Request IDs propagated across services; Merkle roots for batch integrity.  
- Append-only logs for forensic analysis; partitioned BigQuery tables for analytics.

### Security & integrity
- ed25519 signing for events; key rotation and hardware-backed key support.  
- Signed manifests and Merkle anchoring for non-repudiation.  
- Least-privilege IAM, short-lived credentials, automated secret scanning in CI.

### Reliability & scaling
- Idempotent workers with deterministic processing and dedup keys.  
- Queue-based ingestion with adaptive batching and backpressure.  
- Autoscaling thresholds tied to cost/carbon budgets.

### Frontend & UX
- Offline-first patterns: service-worker strategies, local-first data models, conflict resolution.  
- Performance: code-splitting, lazy hydration, Lighthouse-driven budgets.

---

## Architecture snapshot

<pre>
  +---------+      +----------------+      +--------------------+
  | Clients | ---> | Ingestion Queue | ---> | Workers (idempotent)|
  +---------+      +----------------+      +--------------------+
       |                                         |
       |                                         v
       |                                  +-----------------+
       |                                  | Append-only Log |
       |                                  |  (Merkle roots)  |
       |                                  +-----------------+
       |                                         |
       v                                         v
  [ Offline Sync ]                         [ Analytics (BQ) ]
       |                                         |
       v                                         v
  [ Local DB / PWA ]                       [ Dashboards / Alerts ]
</pre>

---
