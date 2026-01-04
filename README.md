# System Risk in Policy Driven AI Systems
System risk and governance analysis of toxicity moderation models using corrected labels, ambiguity-aware evaluation, and fairness diagnostics.

This project was completed as part of a capstone researcch effort at Arizona State University, examining **system-level risk in policy-driven AI systems** through a case study of automated toxicity detection.

Rather than evaluating models solely on accuracy, this project introduces a **risk-based evaluation framework** that surfaces hidden failures in fairness, ambiguity handling, and governance alignment that are obscured by legacy benchmarks.

---

## Research Question
How do data ambiguity, label noise, identity-linked correlations, and evaluation design introduce **system risk** in AI systems used for policy enforcement, and how can governance-aligned evaluation reveal these risks?

---

## System Risk Framework
This project operationalizes **four interrelated dimensions of system risk**:

1. **Origin Risk** – Subjectivity, ambiguity, and inconsistency in human annotations.
2. **Propagation Risk** – Shortcut learning and identity-linked bias inherited from training data. 
3. **Outcome Risk** – Unequal error distribution across identity subgroups.  
4. **Governance Risk** – Inflated model performance under legacy evaluation that collapses under corrected labels.  

---

## Repository Structure
```text
analysis/
├── civil_comments_preprocessing.ipynb
├── system_risk_eda.ipynb
└── golden_dataset_construction/
└── golden_dataset_construction.ipynb

paper/
└── System_Risk_in_Policy_Driven_AI_Systems.pdf

---

## Dataset
- **Primary dataset:** Civil Comments (Jigsaw / TensorFlow Datasets)
- ~2 million online comments annotated for seven harm categories
- No demographic attributes provided → **identity indicators were engineered** using a curated lexicon

## Analysis Components

### 1. Civil Comments Preprocessing
**`analysis/civil_comments_preprocessing.ipynb`**

Prepares the Civil Comments dataset for downstream analysis by:
- selecting relevant labels  
- handling missing values  
- applying minimal text preprocessing  
- producing analysis-ready splits  

> Raw datasets are not included. Users must obtain the Civil Comments dataset under its original license.

---

### 2. System Risk Exploratory Analysis
**`analysis/system_risk_eda.ipynb`**

Explores systemic risks embedded in the dataset, including:
- inter-label inconsistencies  
- text length effects on toxicity prediction  
- identity-term correlations  
- bias signals via pointwise mutual information (PMI)  
- rater disagreement and ambiguity patterns  

This notebook focuses on **risk discovery**, not model optimization.

---

### 3. Golden Dataset Construction
**`analysis/golden_dataset_construction/golden_dataset_construction.ipynb`**

Constructs a governance-aligned **Golden Dataset** designed to expose risks hidden by legacy labels.

Key features:
- risk-focused sampling (borderline, harmful, and clean cases)  
- explicit encoding of annotation ambiguity  
- label expansion and cleaning for evaluation use  

Labeled outputs are intentionally excluded from version control.

---

## Final Report
**`paper/System_Risk_in_Policy_Driven_AI_Systems.pdf`**

The final paper synthesizes findings across preprocessing, exploratory analysis, and Golden Dataset evaluation, with emphasis on:
- fairness–accuracy trade-offs  
- governance failure modes  
- implications for responsible AI deployment  

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

