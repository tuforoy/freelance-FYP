## Source of Truth

Project aim (v1): 
    Develop and evaluate a smart symptom-based risk stratification system for hospital triage using calibrated 3-class predictions derived from ESI, with negation-aware traceable explanations.
Dataset: MIMIC-IV-ED
Text input field: __________ (you will fill later)

Target mapping (frozen v1):
    High = ESI 1–2 
    Medium = ESI 3
    Low = ESI 4–5

Explanations (v1 mode): rule-evidence + extracted symptom evidence (traceable spans)
Models: (1) rule baseline, (2) ClinicalBERT fine-tune only
Calibration: Platt scaling or isotonic (choose later after validation)
Primary offline safety metric: High-risk recall = Recall(High); report High false-negative rate