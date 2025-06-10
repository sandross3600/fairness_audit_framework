# Fairness Metrics Tool

## Purpose

This tool guides teams in selecting, calculating, and interpreting fairness metrics to evaluate AI systems, ensuring alignment with fairness goals (e.g., equal opportunity, predictive parity). It includes statistical validation, intersectional analysis, and visualization templates.

---

## 1. Fairness Metric Selection

Match the selected fairness definition to appropriate metrics:

| Fairness Definition     | Recommended Metric(s)                            | Description                                                       |
|-------------------------|--------------------------------------------------|-------------------------------------------------------------------|
| Statistical Parity      | Demographic Parity Difference                    | Measures positive outcome rate differences across groups          |
| Equal Opportunity       | True Positive Rate Difference                    | Ensures qualified individuals are treated equally                 |
| Equalized Odds          | TPR + FPR Difference                             | Balances both false positives and false negatives                 |
| Predictive Parity       | Positive Predictive Value Difference             | Ensures predictions have equal meaning across groups              |
| Individual Fairness     | Lipschitz Consistency / Similarity-based Gap     | Similar individuals get similar predictions                      |
| Intersectional Fairness | All of the above, computed across intersections  | Reveals disparities hidden in aggregate                          |

---

## 2. Metric Implementation Guidance

### 📊 Basic Setup

For each protected attribute (e.g., gender, race):

- Compare:
  - Positive prediction rates (`P(Ŷ=1|A)`)
  - True positive rates (`P(Ŷ=1|Y=1,A)`)
  - False negative / false positive rates
  - PPV (`P(Y=1|Ŷ=1,A)`)

### ⚙ Tools & Libraries

- Python packages: `fairlearn`, `AIF360`, `scikit-learn`
- Use bootstrap sampling or cross-validation for confidence intervals

---

## 3. Statistical Validation

| Concern                  | Technique                                         |
|--------------------------|--------------------------------------------------|
| Small group size         | Bayesian estimation, hierarchical modeling       |
| Multiple metrics         | Use Benjamini-Hochberg for multiple test control |
| Temporal or random drift | Perform split-wise validation + stress testing   |
| Uncertainty              | Show confidence intervals for each metric        |

---

## 4. Intersectional Fairness

- Compute fairness metrics **across combinations** (e.g., gender + race)
- Use **heatmaps** to visualize disparities
- Flag subgroups with large disparities or high uncertainty

---

## 5. Visualization Templates

### 📊 Disparity Bar Chart

| Group       | Metric (e.g., TPR) | 95% CI          |
|-------------|--------------------|-----------------|
| Group A     | 0.72               | [0.68 – 0.76]   |
| Group B     | 0.58               | [0.50 – 0.66]   |

- Color-code based on thresholds
- Add baseline group reference lines

### 🌐 Intersectional Heatmap

- Rows: Group combinations (e.g., "Black + Female")
- Columns: Metrics (e.g., FNR, PPV)
- Colors: Degree of disparity (red = worse)

---

## 6. Reporting Guidelines

Create fairness dashboards with:

- Metric values + confidence intervals
- Visualizations per protected attribute and intersection
- Disparity explanations with mitigation context
- Significance flags + action recommendations

---

## 7. Case Example: Loan Approval

### Metrics Used

| Metric                        | Value (95% CI)     | Notes                          |
|------------------------------|--------------------|--------------------------------|
| TPR Difference (Black vs White) | 0.09 [0.06–0.12]  | Primary fairness definition    |
| FNR Difference (Low Income)     | 0.12 [0.08–0.16]  | Elevated for minority groups   |
| Demographic Parity Difference   | 0.10 [0.04–0.16]  | Tracked but not optimized      |
| Intersectional TPR (Black + Female) | 0.15 [0.09–0.22] | Hidden without intersectional view |

---

## Tips for Teams

- Always document metric choice rationale
- Compare pre/post-intervention metrics
- Communicate uncertainty clearly
- Track fairness like accuracy: over time, per release

---

## Links to Other Components

- Draws on: Bias Source Identification, Fairness Definition Selection
- Feeds into: Model Remediation, Deployment Impact Review
