# UUDC
Structured Prompts and De-identified Examples for LLM-Based Detection of Unauthorized Use of Doctor’s Code

This repository provides the structured prompt templates and representative de-identified claim-pair examples used for large language model (LLM)–based semantic plausibility assessment in detecting Unauthorized Use of Doctor’s Code in health-insurance claim records.

⚠️ No real-world identifiable medical-insurance data is included.
All examples are de-identified/anonymized (IDs, names, institutions, and other sensitive fields are removed or replaced by placeholders). The released materials are intended solely for academic reproducibility and method illustration under strict data-privacy requirements.

⸻

🔍 Purpose of This Repository

The resources included here are designed to:
	•	guide an LLM to distinguish reasonable medical behaviors from potential unauthorized use in rule-flagged claim record pairs,
	•	enforce structured and deterministic outputs suitable for downstream parsing and audit logging, and
	•	reduce false positives in health-insurance audit workflows.

These materials were used in our study to evaluate LLM behavior under different prompting strategies.

⸻

📂 Contents

1) Prompt Templates

Structured Prompts (S-Prompt)
Templates with explicit reasoning rules and enumerated legitimate scenarios:
	•	Cross-Institution Scenario (S-Prompt)
	•	Cross-Department Scenario (S-Prompt)

Weakly-Structured Prompts (W-Prompt)
Templates providing partial contextual guidance without strict output constraints:
	•	Cross-Institution Scenario (W-Prompt)
	•	Cross-Department Scenario (W-Prompt)

Zero-Prompt Baselines
Minimal task instructions with no prompting structure:
	•	Cross-Institution Zero-Prompt
	•	Cross-Department Zero-Prompt

2) Representative De-identified Examples

A small set of representative de-identified claim-pair inputs covering multiple business scenarios (e.g., inter-institution telemedicine, refund-related re-settlement, emergency–outpatient transitions, and inpatient multi-step procedures).
Each example provides:
	•	the original Chinese de-identified record pair, and
	•	a corresponding English description,
illustrating how structured claim fields are transformed into natural-language inputs for the LLM.

⸻

🧩 How to Use
	1.	Choose an example record pair (or insert your own de-identified pair into the input template).
	2.	Select a prompt setting: S-Prompt, W-Prompt, or Zero-Prompt.
	3.	Call your preferred LLM (local or online), providing the chosen prompt as the system prompt and the formatted record pair as the user input.
	4.	Parse the model output (expected schema):

	•	Legitimate, <scenario-type brief explanation>
	•	Unauthorized use.

⸻

⚠️ Notes on Data Privacy
	•	This repository contains only de-identified examples for illustration and reproducibility.
	•	No raw production data, no identifiable personal information, and no organization-identifying details are released.
	•	Please do not attempt to re-identify any entities from the examples.

⸻

📌 Citation

If you use this repository, please cite our paper (under review at Displays). A formal citation will be added upon acceptance.
