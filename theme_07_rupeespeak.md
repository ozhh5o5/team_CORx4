**Title:** RupeeSpeak — Emotion-Adaptive Multilingual Voice Agent for Financial Inclusion

**Theme:** Theme 7 — Voice-Based AI for Social Impact

**The Problem**

Over 700 million Indians are eligible for government financial schemes but never enroll because information is trapped behind text-heavy English portals. According to [RBI Financial Inclusion data](https://www.rbi.org.in/Scripts/PublicationsView.aspx?id=21479), 190 million adults remain unbanked. Call centers are expensive and inconsistent. IVR systems follow rigid scripts and are universally abandoned mid-call. The [Rupeezy](https://www.rupeezy.in/) Authorized Person program needs to convert inbound partner leads through voice — but existing voice bots sound robotic, ignore emotional cues, and cannot handle real conversational objections.

**What RupeeSpeak Does**

RupeeSpeak is a browser-based AI voice agent that speaks in the user's *native language*, explains financial products conversationally, and handles the **top 5 most common objections** (fees too high, payout concerns, trust issues, competition comparison, "I'll think about it") with natural, empathetic responses. It detects emotional hesitation from the user's voice in real-time and adapts its tone and pace accordingly. It qualifies every lead as Hot/Warm/Cold and hands off Hot leads to a human relationship manager **within 5 minutes** with full conversation context. End-to-end response latency is **under 2 seconds**.

**Core Features**

**1. Sub-2-Second Response Latency** — The full pipeline — speech-to-text, intent classification, response generation, text-to-speech — completes in under 2 seconds end-to-end. This is achieved through streaming STT (partial transcripts trigger intent classification before the user finishes speaking), pre-cached response templates for common objections, and edge-deployed TTS. The conversation feels natural and responsive, not like waiting for a chatbot to think.

**2. Top-5 Objection Handling with Conversational Depth** — The agent does not deflect objections — it resolves them. For *"fees are too high"*, it contextualizes the fee against earning potential with specific numbers. For *"I don't trust online platforms"*, it references SEBI registration and investor protection mechanisms. For *"let me think about it"*, it surfaces a time-limited benefit and offers to schedule a callback. Each objection has 3 levels of depth — if the user pushes back twice, the response escalates in specificity.

**3. Real-Time Acoustic Emotion Recognition** — Analyzes the user's voice *prosody* — pitch contour, speech rate, pause duration, vocal energy — every 2 seconds. Classifies the user's emotional state: confident, confused, frustrated, interested, or disengaged. The agent immediately adjusts: slows down and simplifies when confusion is detected, accelerates and adds enthusiasm when interest spikes. This operates directly on raw audio, not on text transcripts.

**4. Seamless Human Handoff with Full Context** — When a lead is qualified as Hot, the system packages the full conversation transcript, lead score, key objections raised, demographic data, and recommended talking points into a handoff brief. The human relationship manager receives this brief *before* the call is transferred. The transition happens within 5 minutes of qualification. The user does not re-explain anything.

**5. 12-Language Zero-Latency Switching** — Speaks in Kannada, Hindi, Tamil, Telugu, Marathi, Bengali, Gujarati, Malayalam, Punjabi, Odia, Assamese, and English. If the user switches language mid-sentence, the agent follows instantly. There is no "press 2 for Hindi" — language detection and adaptation is automatic and continuous. Built on [AI4Bharat's IndicWhisper](https://ai4bharat.iitm.ac.in/) speech models.

**6. Welfare Scheme Eligibility Engine** — Cross-references the user's demographic data (age, income bracket, location, occupation) against a live database of 200+ central and state schemes from [MyScheme.gov.in](https://www.myscheme.gov.in/). Proactively informs the user of schemes they qualify for but have never applied to. This adds immediate tangible value to the conversation beyond the financial product pitch.

**Who Benefits**

**Rural and semi-urban population (500M+)** get voice-first access to financial products and welfare schemes. **Financial institutions (banks, NBFCs)** achieve automated, empathetic lead qualification at scale. **Government welfare departments** get a direct enrollment pipeline for underutilized schemes. **SHG (Self Help Group) members** receive conversational guidance on credit, insurance, and savings. **Elderly and low-literacy citizens** gain full financial access without reading or typing.

**Key References**

- [RBI Financial Inclusion Reports](https://www.rbi.org.in/Scripts/PublicationsView.aspx?id=21479)
- [MyScheme.gov.in — Government Scheme Discovery](https://www.myscheme.gov.in/)
- [AI4Bharat — Indian Language AI Models](https://ai4bharat.iitm.ac.in/)
- [Deep RL for Dialogue Systems — Research Paper](https://arxiv.org/abs/1709.00103)
- [PMJDY — Pradhan Mantri Jan Dhan Yojana](https://pmjdy.gov.in/)
