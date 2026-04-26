**Title:** SahayakAI — Multimodal Acoustic Triage Console for 1092 Emergency Response

**Theme:** Theme 12 — AI for 1092 Helpline

**The Problem**

India's [1092 women and child distress helpline](https://wcd.nic.in/) handles thousands of calls daily. Operators are overwhelmed, undertrained, and work under extreme time pressure. Callers speak in deep regional dialects, panic-stutter, or mix 3 languages in one sentence — standard speech APIs fail completely. In many critical situations the caller *cannot speak at all* (abusive partner in the room, physical restraint). According to [NCRB data](https://ncrb.gov.in/), crimes against women increased 4% year-on-year, yet helpline response infrastructure has not scaled. The hackathon requires: voice-to-voice understanding, intent recognition, sentiment analysis, **restating the issue to the citizen for confirmation before proceeding**, draft responses for agents, and human-in-the-loop for low-confidence interpretations.

**What SahayakAI Does**

SahayakAI is an AI-powered operator console that transcribes multilingual distress calls in real-time, classifies urgency and intent, performs sentiment analysis, and generates **explainable dispatch recommendations with deterministic causal logic trees**. Before any action is taken, the system **restates the understood issue back to the caller in their own language** for verbal confirmation — ensuring no misinterpretation proceeds to dispatch. For low-confidence interpretations, the system escalates to the human operator with highlighted uncertain segments. When the caller cannot speak, the system analyzes background audio to autonomously estimate situation severity.

**Core Features**

**1. Issue Restatement & Citizen Confirmation Loop** — After transcribing and classifying the caller's issue, the system generates a concise summary in the caller's language and plays it back via TTS: *"Main samajh rahi hoon ki aapke ghar mein koi aapko maarne ki dhamki de raha hai. Kya yeh sahi hai?"* ("I understand someone at your home is threatening to hurt you. Is this correct?"). The caller confirms or corrects. Only after confirmation does the system proceed to dispatch recommendations. This is a non-negotiable requirement from the judges — the system must verify its understanding before acting.

**2. Human-in-the-Loop for Low-Confidence Interpretations** — When the AI's confidence on intent classification falls below 70%, the system does not auto-dispatch. Instead, it highlights the uncertain segments in the transcript, presents the top 3 probable intents with confidence scores, and routes the decision to the human operator. The operator selects the correct intent and the system learns from the correction. This ensures no critical misinterpretation reaches dispatch.

**3. Acoustic Scene Classification for Silent/Dropped Calls** — When a caller dials but cannot speak, the system does not discard the call. An [Acoustic Scene Classification (ASC)](https://dcase.community/) neural network continuously analyzes background audio. It detects specific sound signatures: *physical altercation, vehicle interior, outdoor traffic, construction site, domestic kitchen, crowd*. This non-verbal intelligence is fused with any partial speech to generate an autonomous urgency escalation and approximate environment profile for first responders.

**4. Zero-Resource Deep Dialect NLP** — Standard translation APIs ([Google](https://cloud.google.com/speech-to-text), [Azure](https://azure.microsoft.com/en-us/products/ai-services/speech-to-text)) fail on panicked code-mixed speech. SahayakAI processes raw audio through [phonetic representation models](https://arxiv.org/abs/2006.11477) trained directly on code-switched Indian emergency speech. It bypasses the brittle translate-to-English step entirely and extracts intent, entities (names, locations, threats), and urgency from the native audio waveform. Built on [AI4Bharat IndicWav2Vec](https://ai4bharat.iitm.ac.in/).

**5. Real-Time PII Redaction at Transcription Layer** — The caller's name, address, and Aadhaar number are redacted *the instant they are transcribed* — before the text reaches the classification engine, before it is stored, before any analyst sees it. Raw audio with PII is encrypted and stored separately under access-controlled forensic hold. The working transcript is always clean. Compliant with [DPDP Act 2023](https://www.meity.gov.in/data-protection-framework).

**6. Causal Dispatch Recommendation with Logic Tree** — When the AI recommends dispatching a specific unit (police, ambulance, child welfare, psychiatric support), it presents a deterministic causal logic tree: *"Caller mentioned [knife] + acoustic scene classified as [domestic indoor] + urgency score [9.2/10] → Dispatch: Police + Ambulance."* The operator verifies the logic in under 3 seconds before confirming dispatch. No black-box recommendations — every dispatch suggestion is fully explainable.

**7. Draft Response Generator for Operators** — The system drafts contextual responses for the operator to read or adapt: *calming scripts* for distressed callers, *information gathering prompts* for incomplete reports, and *safety instructions* for immediate-danger situations. The operator can use the draft as-is or modify it. This reduces cognitive load and ensures consistent, protocol-compliant responses even from undertrained operators.

**8. Repeat Caller Pattern Detection & Case Linking** — Maintains a privacy-preserving vectorized voice-print database. When a caller who has called before dials again, the system instantly surfaces their *previous case history, prior dispatch records, and threat escalation trajectory*. Victims do not re-explain their situation from scratch. Chronic abuse patterns are automatically flagged for proactive intervention by child welfare or women's protection officers.

**Who Benefits**

**1092 helpline operators** get reduced cognitive load with AI-assisted triage, draft responses, and explainable dispatch logic in real-time. **Women and children in distress** receive faster, more accurate dispatch — even when they cannot speak. **State Women & Child Development departments** get data-driven resource allocation across districts based on call volume and severity patterns. **Police and emergency response units** receive pre-built situation briefs before arriving on scene. **NGOs working on domestic violence** get anonymized trend data for policy advocacy and intervention planning.

**Key References**

- [Ministry of Women & Child Development — 1092 Helpline](https://wcd.nic.in/)
- [NCRB — National Crime Records Bureau Reports](https://ncrb.gov.in/)
- [DCASE — Acoustic Scene Classification Community](https://dcase.community/)
- [AI4Bharat — IndicWav2Vec Speech Models](https://ai4bharat.iitm.ac.in/)
- [wav2vec 2.0 — Self-Supervised Speech Representations](https://arxiv.org/abs/2006.11477)
- [Digital Personal Data Protection Act 2023](https://www.meity.gov.in/data-protection-framework)
