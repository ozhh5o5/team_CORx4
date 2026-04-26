**Title:** TenderEval AI — Anti-Cartel Forensic Tender Evaluation for Government Procurement

**Theme:** Theme 3 — AI-Based Tender Evaluation and Eligibility Analysis for Government Procurement (CRPF)

**The Problem**

Government tender evaluation in India is manual, opaque, and vulnerable. Officers spend weeks reading thousands of scanned pages. Genuine bidders get disqualified for minor formatting issues while cartels submit coordinated bids through shell companies. According to [CVC Annual Reports](https://cvc.gov.in/), procurement irregularities constitute the largest category of corruption complaints. The core challenge: tender documents define eligibility criteria in unstructured prose, and bidder submissions arrive in every conceivable format — typed PDFs, scanned affidavits, photographed certificates, Word files. No existing system extracts criteria automatically, evaluates bidder evidence against each criterion, or links verdicts to source documents at the page level.

**What TenderEval AI Does**

TenderEval AI ingests the tender document, *automatically extracts every eligibility criterion* without manual pre-labeling, then ingests all bidder submissions across all formats and evaluates each bidder against every criterion. The output is an **explainable, per-criterion verdict** (Eligible / Not Eligible / Needs Review) where every verdict hyperlinks to the *exact page and section* in the bidder's source document that supports or contradicts the claim. No bidder is silently disqualified — every "Not Eligible" verdict ships with the verbatim evidence and a confidence score so officers can verify in seconds.

**Core Features**

**1. Zero-Labeling Criterion Extraction** — The AI reads the tender PDF and extracts every eligibility requirement (minimum turnover, years of experience, license validity, EMD amount, technical certifications) without any manual annotation or pre-training on tender formats. It parses nested conditional requirements (*"if the bidder is an MSME, the turnover threshold is reduced to..."*) into structured criterion objects with thresholds, conditions, and evidence types.

**2. Multi-Format Document Intelligence Pipeline** — Bidder submissions arrive as machine-typed PDFs, handwritten affidavits, scanned certificates with stamps and signatures, rotated/tilted photographs of documents, and Word/Excel files. The pipeline chains OCR, [Vision-Language Models](https://arxiv.org/abs/2304.08485), and layout-aware parsing to extract structured data from every format. No document is rejected for format incompatibility. Handles low-resolution scans, rubber-stamp overlays, and handwritten annotations.

**3. Per-Criterion Verdict with Source-Page Anchoring** — For every eligibility criterion and every bidder, the AI produces a verdict with a confidence score. Each verdict hyperlinks to the *exact page number and bounding box region* in the original bidder PDF that contains the supporting or contradicting evidence. Officers click through to the source, verify in seconds, and override if needed. The override is logged with the officer's justification.

**4. Bid-Rigging Detection via Temporal Graph Neural Networks** — Beyond document evaluation, TenderEval builds a continuously growing knowledge graph of all bidding entities across historical tenders: registered directors, shared addresses, IP submission metadata, bid amount patterns, and win/loss sequences. A [Temporal GNN](https://arxiv.org/abs/2006.10637) detects shell company clusters, round-robin bidding rings, and coordinated price inflation. Every bidder receives a **forensic risk score** visible to evaluation officers.

**5. Live Statutory Cross-Verification** — The AI cross-references bidder claims against live government databases: [GST registration status](https://www.gst.gov.in/), [MSME Udyam registration](https://udyamregistration.gov.in/), blacklisting records on [GeM](https://gem.gov.in/), and active labor law compliance. Discrepancies between claimed and actual status are flagged automatically with the exact conflicting data source cited.

**6. Comparative Bid Matrix with Override Audit** — Officers see a side-by-side comparison of all bidders across all criteria — color-coded pass/fail with drill-down into every supporting document. When an officer overrides the AI's verdict, the system records the override reason, the officer's identity, and the timestamp. The full override history is available to audit.

**Who Benefits**

**CRPF and Defense procurement** get tamper-proof, explainable evaluations with source-linked verdicts. **All central and state procurement bodies** achieve 10x faster evaluation with zero silent disqualifications. **Anti-corruption agencies (CBI, CVC)** get automated cartel detection across historical tenders. **Genuine MSME bidders** receive fair evaluation regardless of document formatting quality. **RTI applicants and investigative journalists** get a complete audit trail for every procurement decision including officer overrides.

**Key References**

- [Central Vigilance Commission — Annual Reports](https://cvc.gov.in/)
- [Government e-Marketplace (GeM)](https://gem.gov.in/)
- [MSME Udyam Registration Portal](https://udyamregistration.gov.in/)
- [GST Taxpayer Search](https://www.gst.gov.in/)
- [Temporal Graph Networks — Research Paper](https://arxiv.org/abs/2006.10637)
- [LLaVA Vision-Language Model — Research Paper](https://arxiv.org/abs/2304.08485)
