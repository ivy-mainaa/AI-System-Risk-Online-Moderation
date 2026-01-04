# AI-System-Risk-Online-Moderation
System risk and governance analysis of toxicity moderation models using corrected labels, ambiguity-aware evaluation, and fairness diagnostics.

# System Risk in Policy-Driven AI Systems  
**A Governance-Aligned Evaluation of Online Content Moderation Models**

This project was completed as part of a capstone researcch effort at Arizona State University, examining **system-level risk in policy-driven AI systems** through a case study of automated toxicity detection.

Rather than evaluating models solely on accuracy, this project introduces a **risk-based evaluation framework** that surfaces hidden failures in fairness, ambiguity handling, and governance alignment that are obscured by legacy benchmarks.

---

## Research Question
How do data ambiguity, label noise, identity-linked correlations, and evaluation design introduce **system risk** in AI systems used for policy enforcement, and how can governance-aligned evaluation reveal these risks?

---

## System Risk Framework
This project operationalizes **four interrelated dimensions of system risk**:

1. **Origin Risk** – Subjectivity, ambiguity, and inconsistency in human annotations  
2. **Propagation Risk** – Shortcut learning and identity-linked bias inherited from training data  
3. **Outcome Risk** – Unequal error distribution across identity subgroups  
4. **Governance Risk** – Inflated model performance under legacy evaluation that collapses under corrected labels  

---

## Dataset
- **Primary dataset:** Civil Comments (Jigsaw / TensorFlow Datasets)
- ~2 million online comments annotated for seven harm categories
- No demographic attributes provided → **identity indicators were engineered** using a curated lexicon

### Golden Dataset (Key Contribution)
To address label noise and ambiguity, we constructed a **Golden Dataset**:
- 310 high-impact, borderline, and ambiguous comments
- Manually re-labeled by two human annotators
- Includes:
  - Corrected harm labels
  - Explicit ambiguity codes
  - Reconstructed agreement fields

This dataset serves as a **governance-aligned benchmark** rather than a conventional test set.

---

## 🛠️ Methods
### Exploratory Risk Diagnostics
- Risk-structured EDA aligned with the four system risk dimensions
- Analyses include:
  - Inter-label correlations
  - Identity term PMI (bias signals)
  - Ambiguity concentration analysis
  - Temporal drift patterns

### Modeling Pipeline
- Baseline: Logistic Regression (TF–IDF)
- Transformer models: **DistilRoBERTa**
- Training on a **1% stratified sample** to manage computational constraints

### Mitigation Strategies
- **Identity Masking** – Removes explicit identity terms from text
- **Sample Reweighting** – Cost-sensitive loss to address class imbalance

---

## Key Results
- Models appear strong under legacy labels (**AUC ≈ 0.84**)
- Performance **drops sharply** when evaluated on the Golden Dataset (**AUC ≈ 0.70**)
- Significant subgroup disparities emerge under corrected labels
- Ambiguous content drives the largest model–human disagreement
- Mitigation strategies reduce some disparities but introduce tradeoffs

**Core finding:**  
Legacy evaluation substantially overstates model reliability and fairness in policy-driven settings.

---

## Governance Implications
- Accuracy alone is insufficient for approving AI systems used in moderation or policy enforcement
- Ambiguity-aware, identity-aware evaluation is essential for trustworthy deployment
- Mitigation techniques must be evaluated under corrected, governance-aligned benchmarks
- The Golden Dataset approach provides a template for auditing real-world AI systems

---

## Repository Structure
```text
ai-system-risk-online-moderation/
├── paper/            # LaTeX source files for the report
├── analysis/         # EDA and system risk diagnostics notebook
├── pdf/              # Final compiled report
├── README.md
└── .gitignore
