# HIVcoPred: Hybrid Approach for HIV-1 Coreceptor Prediction

Welcome to the official documentation for **HIVcoPred**, a high-efficiency computational method for predicting the coreceptor usage (tropism) of HIV-1 based on the third variable (V3) loop amino acid sequence. Identifying whether a strain uses the CCR5 (R5-tropic) or CXCR4 (X4-tropic) coreceptor is vital for the successful management of HIV-infected individuals, particularly before administering CCR5 antagonists like Maraviroc.

**Web Server:** [http://www.imtech.res.in/raghava/hivcopred/](http://www.imtech.res.in/raghava/hivcopred/)(https://webs.iiitd.edu.in/raghava/hivcopred/)

---

## Citation

Kumar, R., & Raghava, G. P. S. (2013).
**Hybrid Approach for Predicting Coreceptor Used by HIV-1 from Its V3 Loop Amino Acid Sequence.**
*PLoS ONE*, 8(4), e61437.
[https://doi.org/10.1371/journal.pone.0061437](https://doi.org/10.1371/journal.pone.0061437)

---

## About the Platform

HIV-1 infection is initiated by interactions between the viral gp120 protein and host cell receptors (CD4) and coreceptors (CCR5 or CXCR4). While existing genotypic methods are highly accurate at predicting CCR5 usage, they often perform poorly for CXCR4 usage. HIVcoPred addresses this challenge using a Hybrid model that combines machine learning (SVM) with similarity-based searching (BLAST).


### Key Research Findings
* **Residue Preferences**: R5-tropic sequences prefer Asparagine (N) and Isoleucine (I), while X4-tropic sequences are dominated by positively charged, large residues like Lysine (K), Arginine (R), and Tryptophan (W).
* **Charge Rule**: X4 tropism is strongly associated with an increase in net positive charge, specifically at positions 11 and 25 of the V3 loop.
* **Hybrid Performance**: The integrated Hybrid model achieved an overall accuracy of 89.19% and a Matthews Correlation Coefficient (MCC) of 0.72.

---

## Features & Model Performance

The platform provides several models developed using various input features and a comprehensive dataset of 1,799 R5-tropic and 598 X4-tropic sequences.

| Method | Sensitivity (%) | Specificity (%) | Accuracy (%) | MCC |
| :--- | :--- | :--- | :--- | :--- |
| **AAC** (Amino Acid Composition) | 88.77 | 76.92 | 85.82 | 0.64 |
| **DPC** (Dipeptide Composition) | 93.50 | 80.43 | 90.24 | 0.74 |
| **SAAC** (Split Amino Acid Comp.) | 88.94 | 81.44 | 87.07 | 0.67 |
| **Binary** (Binary Patterns) | 92.98 | 78.19 | 89.86 | 0.70 |
| **Hybrid** (SAAC + BLAST) | 91.66 | 81.77 | 89.19 | 0.72 |

---

## Technical Overview

### Machine Learning & Algorithms
* **Support Vector Machine (SVM)**: Built using SVM-light V6.01, employing various kernels to classify sequences based on fixed-length numerical vectors.
* **BLAST Integration**: Utilizes similarity searches to refine SVM scores. If a sequence has a highly significant BLAST hit (E-value ≤ 10⁻¹⁷) to a known tropic class, the SVM score is adjusted to improve prediction confidence.
* **SAAC**: Divides the V3 sequence into two parts to capture compositional differences at the N- and C-terminals.

### Sequence Analysis Tools
* **WebLogo**: Displays relative amino acid frequencies to identify conserved positions (e.g., Cysteine residues at terminals).
* **Two Sample Logo (TSL)**: Highlights significant differences between R5 and X4 datasets at specific sites.

---

## Applications

* **Clinical Management**: Assisting clinicians in determining the eligibility of patients for CCR5 antagonist regimes.
* **Subtype Versatility**: Demonstrated high accuracy across various HIV-1 subtypes, including non-B subtypes and subtype D.
* **Dual-Tropic Detection**: Efficiently predicts CXCR4 usage in R5X4-tropic (dual-tropic) sequences, which are often underestimated by other tools.

---

## Contact & Authors

**Dr. Gajendra P. S. Raghava**
Bioinformatics Centre, Institute of Microbial Technology (CSIR), Chandigarh, India.
**Email**: raghava@imtech.res.in

---

## License

This is an open-access project distributed under the terms of the **Creative Commons Attribution License**, which permits unrestricted use and distribution provided the original author and source are credited.
