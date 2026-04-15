# Rastre

**Audit trail infrastructure for AI systems**

Rastre is a platform for recording, storing, and analyzing the events that AI systems produce during operation. It gives developers a structured, compliant audit trail that satisfies the record-keeping obligations of the EU AI Act and related standards &mdash; without building the infrastructure themselves.

## The problem

AI systems operating in regulated environments must log what they do. Article 12 of the EU AI Act mandates record-keeping for high-risk AI systems; ISO/IEC 24970 specifies what those records must contain. But the obligation doesn't stop at storage: organizations must also be able to demonstrate compliance, respond to audits, and monitor system behavior over time.

Building this infrastructure in-house is expensive and non-trivial to get right. Rastre provides it as a service.

## What's live

**Ingest API**  
HTTP endpoint for streaming AI events into Rastre. API-key authenticated, SQS-backed async ingestion &mdash; fire and forget, sub-millisecond acknowledgement. Base URL: `https://api.rastre.dev/v1`. A sandbox is available at `https://sandbox-api.rastre.dev/v1`.

**Audit Trail Storage**  
Immutable, tamper-evident event store. Payloads persisted to S3 with Object Lock, metadata indexed in PostgreSQL &mdash; partitioned by org, audit trail, and date.

**Python SDK**  
Client library that wraps the HTTP API with typed methods mapping to the event categories defined in ISO/IEC 24970 and Article 12: `log_outcome()`, `start_transaction()`, `log_oversight()`, `log_feedback()`, `log_error()`, and others.

**Logbook**  
Web application at `https://log.rastre.dev` for onboarding, audit trail management, and per-event compliance scoring against EU AI Act and ISO/IEC 24970. Every incoming event is scored at the field level so developers can identify specific gaps before going to production.

## How it works

1. Instrument an AI system using the SDK or HTTP API directly.
2. Send events to the sandbox API during development.
3. The Logbook shows incoming events and their compliance scores in real time.
4. Switch to production when ready. Events are stored with a minimum 6-month retention period as required by Art. 26(6) of the EU AI Act.
5. Query and export the audit trail for audits, incident investigations, and internal monitoring.

## Regulations and standards

The primary regulatory driver is the **EU AI Act** (Regulation (EU) 2024/1689), specifically the record-keeping obligations under Article 12. The operative planning deadline for high-risk AI systems (Annex III) is **2 December 2027** &mdash; extended by the Digital Omnibus proposal from the original August 2026 date.

Events are structured per **ISO/IEC 24970**, the international standard for AI system logging.

**GDPR** is a secondary use case: the same audit trail infrastructure that satisfies Article 12 also supports the accountability and integrity obligations under GDPR Arts. 5(2), 24, and 32.

## Roadmap

- **Performance monitoring** &mdash; output drift detection, input distribution shift, and model accuracy tracking against Art. 72 post-market monitoring obligations.
- **Human override analytics** &mdash; intervention rates and override patterns as evidence that oversight is actively functioning (Art. 14).
- **Demonstrable anti-tampering** &mdash; cryptographic hash chain across all events, with verifiable integrity proofs exportable for auditors (Art. 16, 19).
- **Compliance audit package** &mdash; structured export covering a defined period: hash-chain proof, retention certificates, accuracy trends, human override rates, and incident log.
- **Regulatory incident notification** &mdash; auto-generated Art. 73 notifications with submission tracking and deadlines.
