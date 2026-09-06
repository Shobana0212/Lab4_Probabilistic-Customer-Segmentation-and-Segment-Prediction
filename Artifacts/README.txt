MDI3003 LAB 04 — REPRODUCIBILITY README
========================================

Task
----
Supervised multiclass prediction of the predefined customer
Segmentation labels.

Target
------
Segmentation

Observed classes
----------------
A, B, C, D

Features
--------
Gender, Ever_Married, Age, Graduated, Profession, Work_Experience, Spending_Score, Family_Size, Var_1

Feature groups
--------------
Demographic:
Gender, Ever_Married, Age, Graduated, Profession, Family_Size

Psychographic:
None available in the supplied feature set

Behavioral:
Work_Experience, Spending_Score

Other:
Var_1

Combined:
All retained features listed above.

Data provenance
---------------
Training file: Train.csv
Training SHA-256: 4245166ea666055eaeb151aecf2d16c346cdb230749eb064949684c965bf7355
Test SHA-256: None
Source URL: None
Access date (UTC): None

Label provenance
----------------
Segmentation is treated as a predefined supervised target.
The historical/business rule used to create the labels was not
independently reconstructed in this notebook.

Experimental design
-------------------
Train/test split:
- Stratified split
- Test fraction: 20%
- Random state: 42
- The test partition is locked and used only for final evaluation.

Cross-validation:
- StratifiedKFold
- 5 folds
- shuffle=True
- random_state=42

Model selection
---------------
Primary criterion:
Mean five-fold validation Macro F1.

Secondary criterion:
Standard deviation of fold Macro F1.

Selected model:
CategoricalNB_mixed

Mean CV Macro F1:
0.484523

CV Macro F1 SD:
0.010115

Core models
-----------
1. DummyClassifier
2. GaussianNB
3. BernoulliNB
4. CategoricalNB mixed-feature pipeline

Feature ablation
----------------
Demographic, psychographic, behavioral and combined
feature groups were evaluated using the same fixed
cross-validation protocol.

Psychographic status:
No dedicated psychographic variables were available
in the supplied feature set.

Locked-test results
-------------------
Accuracy:
0.5117719950433705

Macro F1:
0.48528393969993966

Weighted F1:
0.4954911555490408

Review policy
-------------
The review/abstention threshold is selected from the
validation-only out-of-fold confidence/error trade-off.
It is frozen before locked-test evaluation.

Selected threshold:
0.5499999999999999

Responsible analytics
---------------------
The workflow documents:
- data minimization
- purpose limitation and consent
- de-identification
- demographic/sensitive attribute review
- possible historical label bias
- fairness assessment
- stereotyping and misuse risks
- uncertainty-aware review
- human oversight
- monitoring and accountability

Important reproducibility rule
------------------------------
Do not tune the model or review threshold using locked-test
performance.

Rerun procedure
---------------
1. Place Train.csv in the expected working directory.
2. Run the notebook from the first cell in order.
3. Keep random seed = 42.
4. Preserve the fixed stratified split.
5. Preserve the five-fold StratifiedKFold configuration.
6. Select the model using validation Macro F1.
7. Freeze the review threshold using validation data only.
8. Evaluate the locked test set only after selection.
9. Confirm that the generated artifacts are non-empty.
10. Reload the saved final model as a fixture test.

Main artifact directory
-----------------------
lab04_outputs/artifacts/

Key files
---------
- reproducibility_manifest.json
- data_quality_audit.json
- label_provenance_circularity_audit.json
- feature_group_ablation.csv
- cv_classwise_metrics.csv
- training_inference_timing.csv
- confusion_matrix_counts.csv
- confusion_matrix_row_normalized.csv
- test_classwise_metrics.csv
- business_operational_error_analysis.csv
- top_five_business_errors.csv
- review_threshold.json
- confidence_coverage_error.csv
- responsible_use.txt
- final_conclusion.txt
- final_summary.json