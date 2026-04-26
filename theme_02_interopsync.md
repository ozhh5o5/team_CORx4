**Title:** InteropSync Karnataka — Self-Healing Semantic Middleware for Government Interoperability

**Theme:** Theme 2 — Two-Way Interoperability between SWS and Department Systems

**The Problem**

Karnataka's [Single Window System (SWS)](https://swskrn.karnataka.gov.in/) connects to 40+ legacy departmental databases built in complete isolation. There is no reliable join key across the State's business data. The same business exists as different records in different databases, and master data cannot be linked. Activity data — inspections, renewals, consumption, compliance events — sits inside each department system and cannot be aggregated per business. Any working solution must sit alongside existing systems — source department systems cannot be modified, re-platformed, or migrated. India's [National e-Governance Plan](https://www.meity.gov.in/divisions/national-e-governance-plan) identifies interoperability as a top-priority challenge, and the [IndEA Framework](https://www.meity.gov.in/writereaddata/files/IndEA_Framework_1.0.pdf) mandates standardized data exchange, yet no production-grade solution exists today.

**What InteropSync Does**

InteropSync Karnataka is a *production-grade bidirectional translation and propagation layer* between SWS and all connected department backends. It uses **UBID (Unique Business ID)** as the sole join key. When a business updates its address in SWS, InteropSync translates that change into the target department's schema and pushes it via the appropriate integration surface — REST API, webhook callback, SFTP file drop, or database polling — depending on what each legacy system supports. When a department issues a new license or inspection result, InteropSync captures it and propagates it back to SWS. Every operation is **idempotent** — replaying the same event produces the same result with no side effects.

**Core Features**

**1. Multi-Surface Integration Engine** — Each department exposes a different integration surface. InteropSync supports four: *REST API push, webhook subscription, scheduled file-snapshot polling, and direct database polling*. The system auto-selects the appropriate transport per department based on a configuration manifest. Adding a new department requires only a manifest entry and a schema mapping — no code changes.

**2. Configurable Schema Translation Layer** — Every department stores business data in incompatible formats. InteropSync maintains a per-department translation map that converts field names, data types, date formats, and enumeration values bidirectionally. The translation map is version-controlled — when a department updates its schema, the old and new maps coexist during a migration window. Fields like *comp_name* in Labour → *enterprise_title* in SWS → *firm_id* in Commercial Tax are translated automatically and deterministically.

**3. Conflict Detection & Resolution with Policy Engine** — When two departments update the same UBID field simultaneously, the system detects the collision. A configurable policy engine resolves it: *latest-timestamp-wins* for low-risk fields (phone numbers), *source-authority-wins* for regulated fields (license status — only the issuing department's update is authoritative), and *escalate-to-human* for high-risk fields (legal entity name changes). Every resolution is logged with the policy that was applied and the data that was rejected.

**4. Tamper-Proof Cryptographic Audit Chain** — Every propagation event — who changed what, when, from which system, which translation map version was used — is hashed into an append-only cryptographic log. This log is independently verifiable by any department, any auditor, any [RTI](https://rti.gov.in/) query. No single department controls the log. No record is deletable.

**5. Retry & Failure Recovery with Dead-Letter Queue** — When a department system is down, the propagation is queued with exponential backoff. After configurable retry exhaustion, the event moves to a dead-letter queue visible on the admin dashboard. Operators manually replay or discard dead-letter events with full audit logging. No data is silently lost.

**6. Offline-First Sync for Rural District Offices** — District-level offices with intermittent connectivity queue all updates locally using an embedded SQLite store. The moment connectivity is restored, InteropSync replays and merges queued changes using vector clocks to detect and resolve ordering conflicts without data loss or duplication.

**7. Department Health Dashboard & SLA Monitoring** — A live command center shows sync health of every connected department: propagation latency (p50/p95/p99), failure rate, schema drift score, pending conflicts, and dead-letter queue depth. Departments that consistently breach SLA thresholds receive automated escalation alerts to their IT nodal officers.

**Who Benefits**

**40+ Karnataka departments** get a single source of truth with zero manual re-entry. **10,000+ businesses using SWS** see approvals clear in hours instead of weeks. **District and taluk offices** participate fully despite poor rural connectivity. **CAG and audit bodies** get a tamper-proof, independently verifiable trail for every data movement. **Citizens filing RTI** get timestamped, hash-verified government action logs.

**Key References**

- [Karnataka Single Window System Portal](https://swskrn.karnataka.gov.in/)
- [National e-Governance Plan — MeitY](https://www.meity.gov.in/divisions/national-e-governance-plan)
- [IndEA (India Enterprise Architecture) Framework](https://www.meity.gov.in/writereaddata/files/IndEA_Framework_1.0.pdf)
- [DoWhy — Causal Inference Library by Microsoft Research](https://www.microsoft.com/en-us/research/project/dowhy-an-end-to-end-library-for-causal-inference/)
