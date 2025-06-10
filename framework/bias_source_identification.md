# Bias Source Identification Tool

## Purpose

This component helps teams systematically identify **where bias can enter the ML lifecycle**, from data collection through deployment. The goal is to proactively detect and address bias at each stage to ensure fair system outcomes.

---

## Common Bias Sources

| Lifecycle Stage      | Type of Bias                | Description                                                                 |
|----------------------|-----------------------------|-----------------------------------------------------------------------------|
| Data Collection       | Historical Bias             | Data reflects past discrimination (e.g., lending, hiring)                   |
|                      | Representation Bias         | Under-sampling of certain groups                                            |
| Data Labeling         | Label Bias                  | Subjective or inconsistently applied labels across groups                   |
| Feature Engineering   | Measurement Bias            | Features proxy for protected attributes (e.g., ZIP code for race)           |
| Model Training        | Optimization Bias           | Loss functions that ignore fairness or amplify existing disparities         |
|                       | Aggregation Bias            | Ignoring relevant subgroup differences                                     |
| Model Evaluation      | Evaluation Bias             | Using aggregate metrics that mask disparities                              |
| Deployment            | Feedback Loops              | System behavior shifts user input or future data                           |
|                       | External Use Misalignment   | Real-world use diverges from training assumptions                           |

---

## How to Use This Component

### Step 1: Conduct Pipeline Audit

For your system (e.g., loan approval), go stage by stage:

1. **Where does the data come from?**
2. **Who labels it and how?**
3. **What features are derived or transformed?**
4. **What loss function or objective is used?**
5. **How are models evaluated before deployment?**
6. **What happens after deployment – how are predictions used?**

### Step 2: Identify Bias Risks

| Stage             | Risk Identified                          | Example                                                            |
|------------------|------------------------------------------|--------------------------------------------------------------------|
| Data Collection   | Under-sampling rural applicants           | Model underpredicts for rural regions                              |
| Feature Design    | Income-to-loan ratio influenced by race   | Model indirectly encodes race                                      |
| Training          | Optimizing for accuracy only              | Disparities in false negatives across groups                       |
| Deployment        | Model used without human review           | Minority applicants denied without recourse                        |

### Step 3: Document Findings

| Component         | Bias Type             | Evidence / Concern                           | Mitigation Plan                         |
|------------------|------------------------|-----------------------------------------------|------------------------------------------|
| Income Feature    | Measurement Bias       | Strongly correlated with race                 | Evaluate alternatives / fairness constraint |
| Prior Approvals   | Historical Bias        | Reflects past redlining practices             | Reweight or de-bias training labels        |

---

## Example: Loan Approval System

- **Data bias**: Historical loan data excluded applicants from majority-minority ZIP codes.
- **Labeling bias**: Approval history used as label, reflecting biased human decisions.
- **Feature bias**: Debt-to-income ratio indirectly encodes systemic income disparities.
- **Evaluation bias**: Initial metrics ignored true positive disparities.

**Mitigation**: Debias training labels, audit features, introduce fairness-aware loss functions, and apply post-processing on thresholds.

---

## Tips for Teams

- Work cross-functionally: engage product, data science, domain experts.
- Include intersectional analysis at each stage.
- Trace impacts forward: how does early-stage bias affect outcomes?

---

## How This Connects

⬇ Outputs feed into:
- **Fairness Metrics Tool**
- **Model constraints or feature reviews**

⬆ Inputs include:
- Historical Context Summary
- Fairness Definitions selected
