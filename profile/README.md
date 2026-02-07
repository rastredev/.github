# Rastre

Rastre provides audit logging infrastructure for applications that need to record and demonstrate accountability around data &mdash; who accessed what information, who modified records, who granted permissions, and who performed sensitive operations.

Whether you're answering "who accessed this customer's personal data?" during a GDPR request, demonstrating your data governance practices in enterprise sales, preparing for compliance audits, or investigating a data modification incident, Rastre gives you reliable records of data-related events.

---

**Data-centric accountability**  
Record who accessed, modified, exported, or deleted specific data records. Not general product analytics &mdash; focused audit trails for demonstrating data governance and protection practices required by GDPR, HIPAA, and modern data protection regulations.

**Built for data investigations**  
When you need to answer "who accessed patient record #12345 last month" or "who changed this customer's billing address," you have complete, traceable history. Every event includes the full context needed to reconstruct what happened and demonstrate compliance with data protection requirements.

**Anti-tampering protection**  
Audit records are immutable &mdash; stored using write-once mechanisms that make modification or deletion technically impossible after recording. Meets regulatory requirements for data integrity under frameworks like NIS2, DORA, and 21 CFR Part 11.

**Privacy by design**  
Tokenization replaces user identities before events reach Rastre's infrastructure. Organizations maintain token-to-identity mappings in their own systems, giving them control over PII while preserving analyzable event data for compliance reporting and operational analysis.

**Multi-environment by default**  
Separate audit trails for sandbox vs production. Different compliance requirements for different event types. Different retention policies per customer. Designed from the ground up for SaaS applications serving regulated industries with diverse compliance needs.

---

## Use Cases

**EU AI Act compliance for high-risk AI systems**  
The EU AI Act (Article 12) mandates automatic event logging for all high-risk AI systems &mdash; including medical AI, HR decision systems, credit scoring, and law enforcement tools. Organizations deploying these systems must maintain tamper-proof audit trails showing who invoked the AI, what data was processed, which models were used, what decisions were made, and whether humans verified outputs.

Consider a clinical research platform that uses LLMs to extract structured data from patient records: Article 12 requires logging every document processed, every model invocation, extraction success rates, confidence scores, human verification actions, system errors, and model version changes. These logs must be retained for six months minimum (Article 19), enable post-market monitoring (Article 72), and support operational oversight by deployers (Article 26). Penalties for non-compliance reach €15 million or 3% of global turnover.

Rastre provides the audit infrastructure these systems need: automatic event capture at the application layer, immutable storage meeting regulatory requirements, tokenized actor identities protecting PII while preserving accountability, and structured metadata enabling both compliance reporting and operational analysis. Organizations building high-risk AI systems can integrate Rastre to satisfy Article 12's logging mandate without building custom audit infrastructure or storing sensitive personal data in their logs.
