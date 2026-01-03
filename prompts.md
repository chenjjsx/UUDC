Prompts for Unauthorized Use of Doctor’s Code Detection

=======================================================

A. Cross-Institution Scenario

-----------------------------

A1. Structured Prompt (S-Prompt) — Cross-Institution

[CrossInstitution_SPrompt]

Task: Determine whether the flagged record pair represents a reasonable medical behavior or an unauthorized use of doctor’s code. The pair is flagged because the time interval between two records from different institutions is below a predefined threshold.

Certain situations may still be reasonable. Evaluate the structured fields and identify whether the case belongs to one of the legitimate scenarios below:

Telemedicine cross-institution services: If one record shows the “Internet Hospital” payment-location category, the behavior may reflect platform-approved remote collaboration.

Claim resubmission after patient refund: If the patient has a refunded claim record within the past week, the current claim may be a re-submission initiated by the patient and not caused by the doctor, thus reasonable.

If other fields suggest a reasonable scenario, briefly state it.

Decision rules:

If any reasonable scenario applies → output “Reasonable, ”
Otherwise → output “Unauthorized.”
Output Format (must follow exactly one):

Reasonable,
Unauthorized
Do NOT use uncertain expressions such as “suggest,” “possible,” “maybe,” or “needs further manual review.”

A2. Weakly-Structured Prompt (W-Prompt) — Cross-Institution

[CrossInstitution_WPrompt]

If a doctor appears in two different institutions within a time interval shorter than the threshold, the case is flagged as suspicious.

However, in some situations the behavior may still be reasonable. Consider:

Telemedicine cross-institution diagnosis via an Internet Hospital platform.
Claim resubmission after a refunded claim within the past week.
If other structured fields indicate a reasonable explanation, describe it briefly.

Otherwise treat the case as a suspected unauthorized use of doctor’s code.

A3. Zero-Prompt — Cross-Institution

[CrossInstitution_ZeroPrompt]

A doctor appears in two different institutions within a very short time interval, which may indicate unauthorized use of doctor’s code. In some special cases the behavior may still be reasonable, depending on the structured fields.

Please determine whether the behavior is reasonable or unauthorized, and briefly explain your reasoning.

B. Cross-Department Scenario (Same Institution)

----------------------------------------------

B1. Structured Prompt (S-Prompt) — Cross-Department

[CrossDepartment_SPrompt]

Task: Determine whether the flagged record pair represents a reasonable medical behavior or unauthorized use of doctor’s code. The pair is flagged because the time interval between two records from different departments within the same institution is below the threshold.

Some situations may still be reasonable. Exclude the following legitimate scenarios:

Rapid transitions between outpatient and emergency: If one record belongs to Emergency, the case may reflect a normal outpatient-to-emergency transfer or urgent treatment.

Multistep inpatient clinical workflow: If the patient is in an inpatient status, the behavior may involve department transfer, consultation, or joint diagnosis.

Telemedicine cross-department collaboration: If any record shows the “Internet Hospital” payment-location category, the case may reflect remote multi-department collaboration within the platform.

Claim resubmission after refund: If there is a refunded claim for the same patient within the past week, the current record may be a re-submission initiated by the patient and not caused by the doctor, thus reasonable.

If other structured fields indicate a special and reasonable scenario, describe it briefly.

Important: Evaluate all records of this doctor within the relevant time window (i.e., multiple claims), and make a holistic judgment rather than judging a single claim in isolation.

Output Format (must follow exactly one):

Reasonable,
Unauthorized
Do NOT use uncertain expressions such as “suggest,” “possible,” “maybe,” or “needs further manual review.”

B2. Weakly-Structured Prompt (W-Prompt) — Cross-Department

[CrossDepartment_WPrompt]

If a doctor appears in multiple departments of the same institution within a short time interval, the behavior is flagged as suspicious.

However, the following conditions may indicate reasonable behavior:

Rapid outpatient–emergency diagnostic flow.
Multistep inpatient treatment processes, including department transfer or joint diagnosis.
Internet Hospital cross-department diagnosis or collaboration.
Claim resubmission following a refunded claim for the same patient within the past week.
If other structured fields support a reasonable explanation, describe it briefly. Otherwise, treat the case as a suspected unauthorized use of doctor’s code.

B3. Zero-Prompt — Cross-Department

[CrossDepartment_ZeroPrompt]

A doctor appears in multiple departments within the same institution in a very short time interval, which may indicate unauthorized use of doctor’s code. In some situations the behavior may still be reasonable, depending on the structured fields.

Please determine whether the behavior is reasonable or unauthorized, and provide a brief explanation.
