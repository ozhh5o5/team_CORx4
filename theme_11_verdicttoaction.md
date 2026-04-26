**Title:** Verdict→Action — Legal Entailment Engine for Court Judgment Compliance

**Theme:** Theme 11 — Court Judgment Action Tracker

**The Problem**

Indian courts issue thousands of judgments annually directing government departments to act — build infrastructure, compensate victims, shut down polluting factories. These orders are buried in dense 50–200 page PDFs written in complex legal prose with layered conditional directives. Departments miss deadlines, misinterpret obligations, and face contempt of court proceedings. According to [National Judicial Data Grid](https://njdg.ecourts.gov.in/) statistics, lakhs of cases involve pending compliance. Judges require a system that extracts structured data (Case ID, Date, Parties, specific orders/directions), generates action plans, and provides a *side-by-side dashboard* for human verification with links back to the original judgment text.

**What Verdict→Action Does**

Verdict→Action ingests court judgment PDFs (typed and scanned), extracts every specific obligation — *Case ID, judgment date, petitioner/respondent names, specific directions, deadlines, and responsible authorities* — using **Legal-BERT with Chain-of-Thought reasoning**. Every extracted obligation is hyperlinked to the *exact paragraph and page* in the original PDF so officers can verify the AI's interpretation against the source text in a side-by-side view. Before execution, the platform cross-references obligations against existing state laws to flag statutory contradictions. Officers verify, assign, and track compliance through a structured escalation workflow with real-time contempt risk scoring.

**Core Features**

**1. Structured Extraction: Case ID, Parties, Orders, Deadlines** — The AI extracts every structured field the judges require: *Case ID/citation, judgment date, bench composition, petitioner names, respondent departments, specific directions/orders, compliance deadlines, and named responsible authorities*. Each field is extracted as a typed, structured object — not free text. Conditional and layered directives (*"if the State fails to comply within 90 days, the Commissioner shall..."*) are decomposed into separate obligation objects with trigger conditions.

**2. Side-by-Side Verification Dashboard with Source Linking** — Officers see the extracted action plan on the left and the original judgment PDF on the right. Every extracted obligation is hyperlinked to the exact paragraph and page in the source PDF. Clicking an obligation scrolls the PDF viewer to the corresponding text, highlighted in context. Officers verify, approve, or correct each extraction before it enters the compliance workflow. This is the core UX requirement from the judges — human verification with full source traceability.

**3. Legal-BERT + Chain-of-Thought Reasoning** — Uses fine-tuned [Legal-BERT](https://arxiv.org/abs/2010.02559) with explicit Chain-of-Thought prompting. The AI traces its reasoning step-by-step: *"Paragraph 42 states 'the respondent State shall ensure...', which identifies the respondent as [Department X]. The phrase 'within six months from the date of this order' sets the deadline at [Date Y]."* Every extraction ships with the reasoning chain as an auditable artifact. Officers see *how* the AI reached its interpretation, not just the result.

**4. Statutory Contradiction Detection** — Before a department executes a court-ordered action, the platform cross-references it against a vector database of existing state legislative acts, departmental circulars, and SOPs. If the court order directs an action that contradicts an existing statute (e.g., *"demolish structure X"* vs. heritage protection act), the system flags the *exact conflicting provisions* with citations from both the judgment and the statute.

**5. Multi-Party Compliance Tracker with Automated Escalation** — Each judgment spawns a compliance project. Every obligation becomes a task card assigned to a specific officer with a hard deadline. Overdue tasks trigger automated escalation: *assigned officer → department secretary → chief secretary → Advocate General's office*. The escalation chain is configurable per department and per urgency level.

**6. Contempt Risk Scoring** — Continuously calculates a real-time **Contempt Risk Score** for every active judgment based on: (a) number of overdue obligations, (b) days past deadline, (c) historical compliance rate of the assigned department, (d) severity of the original order. Departments with rising contempt risk scores are surfaced on a priority dashboard for the Chief Secretary's office.

**Who Benefits**

**State law departments and the Advocate General** get automated extraction that eliminates manual reading of thousands of pages with full source verification. **Department secretaries** receive clear, deadline-bound task assignments from every judgment. **The Chief Secretary's office** gets a real-time contempt risk dashboard across all departments. **High Court and Supreme Court registries** receive structured compliance reporting from the executive branch. **Citizens and PIL petitioners** get verifiable tracking of whether court-ordered relief is executed.

**Key References**

- [National Judicial Data Grid (NJDG)](https://njdg.ecourts.gov.in/)
- [Indian Kanoon — Free Indian Law](https://indiankanoon.org/)
- [SCC Online — Supreme Court Cases](https://www.scconline.com/)
- [Legal-BERT — Research Paper](https://arxiv.org/abs/2010.02559)
- [e-Courts Services Portal](https://ecourts.gov.in/)
