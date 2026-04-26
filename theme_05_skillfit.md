**Title:** SkillFit AI — Bias-Proof Multilingual Video Assessment for Workforce Fitment

**Theme:** Theme 5 — AI SkillFit (Video Assessment for Workforce Fitment)

**The Problem**

India's [Skill India Mission](https://www.skillindia.gov.in/) trains millions annually but placement rates remain low because fitment assessment is either absent or biased. Corporate ATS tools like [HireVue](https://www.hirevue.com/) penalize candidates with regional accents, poor camera quality, or non-English fluency. According to [NSDC data](https://nsdcindia.org/), rural youth who possess strong vocational skills get filtered out before a human ever reviews them. Existing assessment platforms offer no protection against cheating or impersonation, provide no explainability for scores, and fail on code-mixed Indian speech.

**What SkillFit AI Does**

SkillFit AI conducts automated video interviews in the candidate's *native language* (Kannada-first, expandable to 12+ Indian languages). It evaluates domain knowledge, communication clarity, cognitive reasoning, and behavioral composure. The AI is **architecturally debiased** — it mathematically strips out signals correlated with socioeconomic background (accent, lighting, camera resolution, clothing) and scores purely on skill and aptitude. Every score is fully explainable — the candidate and employer see exactly which criteria contributed and by how much.

**Core Features**

**1. Adversarial Debiasing Architecture** — The assessment model contains an adversarial head trained to predict the candidate's socioeconomic tier from internal representations. The main model is *penalized* whenever this prediction succeeds, forcing it to learn skill-only features. This provides a [mathematically provable fairness guarantee](https://arxiv.org/abs/1801.04378) across rural and urban candidates. [HireVue](https://www.hirevue.com/) and [Talview](https://www.talview.com/) analyze video but do not implement adversarial debiasing — they actively penalize poor video quality and regional accents.

**2. Anti-Cheating & Impersonation Detection** — The system continuously monitors for cheating throughout the interview: *face-match verification* confirms the same person who registered is answering, *gaze tracking* detects off-screen reading, *lip-sync analysis* catches pre-recorded audio playback, and *tab-switch detection* flags browser context changes. If impersonation is detected mid-interview, the session is flagged and the specific timestamps are marked for human review. This is a non-negotiable for any government-scale assessment.

**3. Code-Mixed Speech Understanding Engine** — Indian candidates mix Kannada + English + local slang in a single sentence. SkillFit processes raw audio through [phonetic representation models](https://arxiv.org/abs/2006.11477) trained specifically on code-switched Indian speech. It bypasses the brittle translate-then-analyze pipeline that fails on mixed speech entirely. Standard APIs like [Google Speech-to-Text](https://cloud.google.com/speech-to-text) fail on heavily code-switched utterances.

**4. Explainable Score Breakdown** — Every candidate receives a detailed score card showing exactly which competency dimensions contributed to their final score and by how much: *domain knowledge (40%), communication clarity (20%), cognitive reasoning (25%), behavioral composure (15%)*. Each dimension shows the specific questions that drove the score up or down, with direct quotes from the candidate's responses. Officers and candidates both see the same breakdown — no black-box scoring.

**5. Adaptive Difficulty Calibration** — The interview dynamically adjusts question difficulty based on the candidate's real-time performance. If a candidate answers foundational questions confidently, the AI escalates to advanced scenario-based questions. If the candidate struggles, it shifts to gauge baseline competency. Every candidate is assessed at their *true skill ceiling*, not at a fixed difficulty level.

**6. Physiological Composure Analysis via rPPG** — The video feed is analyzed using [remote Photoplethysmography (rPPG)](https://arxiv.org/abs/1905.02419) — extracting micro-fluctuations in facial skin color to estimate heart rate variability. This measures the candidate's stress response to pressure questions *without any wearable device*. The composure score is fused with NLP analysis to produce a holistic behavioral profile.

**7. Employer-Ready Fitment Report with Role Matching** — The output is not a pass/fail. It is a detailed competency radar chart mapped against specific industry roles (CNC operator, healthcare aide, logistics coordinator). Employers receive a ranked shortlist with each candidate's strengths, gaps, and recommended upskilling paths aligned to [NSQF](https://www.nsqfindia.org/) levels.

**Who Benefits**

**State skill development missions (KSDM)** get automated, fair, cheat-proof assessment at scale for all trainees. **ITI and polytechnic graduates** receive bias-free evaluation regardless of accent or camera quality. **Rural youth in Tier 3/4 towns** gain access to jobs that corporate ATS systems currently block. **Employers in manufacturing, healthcare, and logistics** receive pre-screened, role-matched candidates with explainable competency data. **NSDC and Skill India Mission** get data-driven placement analytics across all skill verticals.

**Key References**

- [Skill India Mission](https://www.skillindia.gov.in/)
- [NSDC — National Skill Development Corporation](https://nsdcindia.org/)
- [NSQF — National Skill Qualification Framework](https://www.nsqfindia.org/)
- [Adversarial Representation Learning for Fairness](https://arxiv.org/abs/1801.04378)
- [Remote Photoplethysmography (rPPG) — Research Paper](https://arxiv.org/abs/1905.02419)
- [wav2vec 2.0 — Self-Supervised Speech Representations](https://arxiv.org/abs/2006.11477)
