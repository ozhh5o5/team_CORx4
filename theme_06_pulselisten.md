**Title:** PulseListen AI — Zero-Shot Pharmacovigilance & Outbreak Signal Detection

**Theme:** Theme 6 — Real-Time Social Listening for Patient Experience & Safety Signals

**The Problem**

Adverse drug reactions and disease outbreaks surface on social media days before they appear in hospital databases. India's [CDSCO](https://cdsco.gov.in/) relies on voluntary hospital reporting — a system with massive underreporting. Current monitoring tools use keyword dictionaries — they detect only *known* side effects and completely miss novel signals. When a new drug produces an undocumented reaction, existing systems are blind until patients file formal complaints. Meanwhile, raw social data is riddled with Protected Health Information (PHI) that makes centralized storage a legal liability under India's [Digital Personal Data Protection Act 2023](https://www.meity.gov.in/data-protection-framework).

**What PulseListen AI Does**

PulseListen AI is a *configurable, privacy-first social listening platform* for healthcare organizations. It ingests mentions from X/Twitter, Reddit, regional forums, and news feeds through a **generic data acquisition engine** with configurable keyword sets and source lists. It redacts all PHI and PII at the ingestion edge before data reaches the analysis server. It then runs **Zero-Shot classification** to detect novel, previously uncatalogued adverse events — side effects not in any existing dictionary — without requiring retraining. Every detected signal is surfaced with supporting post evidence, geographic heatmaps, and temporal trend charts through project-level review workflows.

**Core Features**

**1. Generic Configurable Data Acquisition Engine** — The ingestion layer is source-agnostic. Healthcare teams configure keyword sets (drug names, symptom terms, brand names), source lists (specific subreddits, Twitter handles, forum URLs), and ingestion frequency through a project dashboard. Adding a new drug or condition to monitor requires zero code changes — only a configuration update. The same engine adapts to pharmacovigilance, patient experience monitoring, and disease surveillance use cases.

**2. Edge-First PHI/PII Redaction** — Sensitive patient data — names, hospital names, medication dosages linked to individuals — is stripped out by a lightweight NER model running *directly inside the ingestion scraper node*. The centralized analysis server never sees raw personal data. This is architecturally enforced privacy, not post-processing redaction. Compliant with [DPDP Act 2023](https://www.meity.gov.in/data-protection-framework) by design.

**3. Zero-Shot Novel Adverse Event Detection** — Standard pharmacovigilance tools match posts against [MedDRA](https://www.meddra.org/) term lists and miss anything new. PulseListen embeds posts into a continuous semantic vector space and identifies clusters of patient complaints that do *not match any known adverse event term*. These novel clusters are surfaced as **Emerging Unknown Signals** with supporting post evidence. The system detects side effects that drug manufacturers have never documented — without any retraining or dictionary updates.

**4. Multilingual Indian Language Pipeline** — The ingestion pipeline processes posts in Hindi, Kannada, Tamil, Telugu, Bengali, Marathi, and English *natively*. It runs entity extraction and sentiment analysis directly in the source language using multilingual models like [IndicBERT](https://ai4bharat.iitm.ac.in/indicbert) to preserve medical context that translation destroys. A patient describing *"dawai khane ke baad chakkar aa rahe hain"* (dizziness after taking medicine) is processed in Hindi directly.

**5. Temporal Graph Diffusion Engine** — A [Temporal Graph Network](https://arxiv.org/abs/2006.10637) models the propagation pattern of every detected signal across social networks. Genuine outbreak signals show geographic clustering with organic, slow-burn diffusion from diverse accounts. Misinformation shows rapid, bot-amplified spread from a small number of seed accounts. The engine labels every signal as *Verified Cluster* or *Misinformation Flag* with the diffusion graph as visual evidence.

**6. Regulatory-Grade ICSR Report Generator** — Every verified signal automatically compiles into a structured [ICSR (Individual Case Safety Report)](https://www.who.int/teams/regulation-prequalification/regulation-and-safety/pharmacovigilance) format directly submittable to [CDSCO](https://cdsco.gov.in/) or [WHO VigiBase](https://www.who-umc.org/vigibase/vigibase/). Includes redacted patient narrative, source post evidence, temporal trend chart, geographic heatmap, and severity classification.

**Who Benefits**

**CDSCO and Indian drug regulators** get early warning on novel adverse reactions with ready-to-file ICSR reports. **Pharma companies** detect unlisted side effects before they become lawsuits or public crises. **State health departments** get real-time outbreak detection from social signals. **WHO and global health bodies** receive structured ICSR feeds from India's 800M+ internet users. **Hospital patient safety teams** track community sentiment for specific treatments and procedures.

**Key References**

- [CDSCO — Central Drugs Standard Control Organisation](https://cdsco.gov.in/)
- [MedDRA — Medical Dictionary for Regulatory Activities](https://www.meddra.org/)
- [WHO VigiBase — Global Pharmacovigilance Database](https://www.who-umc.org/vigibase/vigibase/)
- [Digital Personal Data Protection Act 2023 — MeitY](https://www.meity.gov.in/data-protection-framework)
- [IndicBERT — AI4Bharat Multilingual Model](https://ai4bharat.iitm.ac.in/indicbert)
- [Temporal Graph Networks — Research Paper](https://arxiv.org/abs/2006.10637)
