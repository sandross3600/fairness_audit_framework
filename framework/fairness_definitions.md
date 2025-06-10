# Fairness Definition Selection Tool

## Purpose

This component helps teams select appropriate **fairness definitions** based on ethical priorities, legal obligations, and system-specific risks identified during the Historical Context Assessment.

## Key Fairness Definitions

| Fairness Definition     | Description                                                                 | Suitable When...                                                                 |
|-------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| Statistical Parity      | Equal probability of positive outcome across groups                        | Equal representation in outcomes is the goal                                     |
| Equal Opportunity       | Equal true positive rate across groups                                     | Concerned with fair access for qualified individuals                            |
| Equalized Odds          | Equal TPR and FPR across groups                                            | False positives and false negatives both carry significant impact                |
| Predictive Parity       | Equal positive predictive value across groups                              | Stakeholders rely on prediction reliability                                     |
| Individual Fairness     | Similar individuals receive similar outcomes                               | Context-specific similarity matters more than group-level parity                |
| Counterfactual Fairness | Predictions do not change when protected attribute is counterfactually flipped | Legal or ethical norms require identity-blind treatment                         |

---

## How to Use This Component

### Step 1: Identify Fairness Priorities

Refer to your Historical Context Summary. Consider:

- Impacted groups  
- Legal constraints (e.g., ECOA, Title VII)  
- Public or organizational values  
- System consequences (e.g., loan denial vs. false arrest)

### Step 2: Use the Decision Matrix

| Priority                               | Recommended Metric Type          |
|----------------------------------------|----------------------------------|
| Representation across groups           | Statistical Parity               |
| Fair treatment for qualified users     | Equal Opportunity                |
| Balancing errors across groups         | Equalized Odds                   |
| Consistent meaning of predictions      | Predictive Parity                |
| Ethical concern with individual cases  | Individual Fairness              |
| Causal fairness despite historical bias| Counterfactual Fairness          |

Select **multiple metrics** where needed to triangulate.

### Step 3: Document Your Selection

| Selected Definition  | Justification                                                  |
|----------------------|---------------------------------------------------------------|
| Equal Opportunity     | Past discrimination against qualified applicants from group X |
| Equalized Odds        | Model errors are high-stakes (false approvals = financial loss) |
| Predictive Parity     | Loan approval decisions must mean the same across groups      |

---

## Example: Loan Approval System

- **Primary Definition**: Equal Opportunity – to ensure qualified borrowers from all demographics have equal access.  
- **Secondary Definition**: Predictive Parity – to ensure the same reliability of approvals across groups.  
- **Justification**: Historical exclusion of minority borrowers despite repayment ability; stakeholders demand confidence in approved loans.

---

## Tips for Teams

- Use intersectional reasoning: different fairness goals may apply to different subgroups.  
- Consult compliance or legal counsel for regulated domains.  
- Document trade-offs transparently when goals conflict.

---

## How This Connects

⬇ Outputs from this step feed into:
- **Fairness Metrics Tool**
- **Bias Source Identification**
- **Model training and evaluation choices**

⬆ Inputs include:
- Historical Context Summary
- Stakeholder values
