# Network_FB100_Project-ZHAO_ZHENYI

README — Network Analysis Project (FB100 Dataset)
=================================================
Author: Zhao Zhenyi

This repository contains the full codebase and results for a Network Analysis homework
based on the Facebook100 (FB100) datasets. Each question (Q2–Q6) is implemented as an
independent Python script, with corresponding result folders for reproducibility
and clarity.

--------------------------------------------------
Project Structure Overview
--------------------------------------------------

analysis_q2.py
analysis_q3.py
analysis_q4.py
analysis_q5.py
analysis_q6.py
data/
results_q2/
results_q3/
results_q4/
results_q5/
results_q6/
plot_q4_case_study.py
Homework_Network_Analysis.pdf

--------------------------------------------------
Data Folder
--------------------------------------------------

data/
  Contains the raw Facebook100 network files (.gml format).
  Each file corresponds to a university Facebook network, with:
    - nodes = students
    - edges = friendship links
    - node attributes = dorm, major, year, gender, etc.

These files are used as input for all analysis scripts (Q2–Q6).

--------------------------------------------------
Question 2 — Basic Network Statistics
--------------------------------------------------

Script:
  analysis_q2.py

Purpose:
  Compute basic structural properties of Facebook university networks,
  focusing on the largest connected component (LCC).

Main operations:
  - Load .gml networks
  - Extract the largest connected component
  - Compute:
      * number of nodes and edges
      * network density
      * global clustering coefficient (transitivity)
      * average local clustering
  - Plot:
      * degree distribution (linear and log-log)
      * degree vs. local clustering coefficient

Outputs:
  results_q2/
    ├── figures/
    │     ├── q2_degree_linear_*.pdf
    │     ├── q2_degree_loglog_*.pdf
    │     └── q2_degree_vs_clustering_*.pdf
    ├── q2_metrics.csv
    └── q2_table.tex

--------------------------------------------------
Question 3 — (Corresponding Analysis)
--------------------------------------------------

Script:
  analysis_q3.py

Purpose:
  Perform the analysis required in Question 3 of the homework.
  (Typically related to network robustness, path lengths, or centrality,
   depending on the assignment statement.)

Outputs:
  results_q3/
    Contains all figures, CSV files, and tables generated for Q3.

--------------------------------------------------
Question 4 — Link Prediction / Case Study
--------------------------------------------------

Scripts:
  analysis_q4.py
  plot_q4_case_study.py

Purpose:
  Study link prediction performance under different settings and parameters.

Main operations:
  - Evaluate prediction metrics (Precision@k, Recall@k)
  - Compare performance as a function of k and fraction of removed edges
  - Perform a focused case study visualization

Outputs:
  results_q4/
    ├── q4_results.csv
    ├── figures/
    │     ├── q4_precision_vs_k_*.pdf
    │     └── q4_recall_vs_k_*.pdf

--------------------------------------------------
Question 5 — Node Classification via Label Propagation
--------------------------------------------------

Script:
  analysis_q5.py

Purpose:
  Recover missing node attributes using label propagation for node classification,
  following the random-walk-based algorithm described in Bhagat et al. (2011).

Key methodological choices:
  - Algorithm: Label Propagation (LP-Zhu), based on random walks
  - Tools:
      * NetworkX for graph handling
      * PyTorch for matrix-based propagation
  - Attributes studied:
      * dorm
      * major
      * gender
  - Missing label simulation:
      * 10%, 20%, 30% of labels randomly removed

Evaluation metrics:
  - Accuracy (as defined in the assignment)
  - Mean Absolute Error (MAE, interpreted as 0/1 classification error)

Outputs:
  results_q5/
    ├── q5_summary_all_schools_long.csv
    ├── q5_table1_duke_accuracy.tex
    ├── q5_table1_duke_mae.tex
    ├── q5_global_accuracy.tex
    ├── q5_global_mae.tex
    └── figures/
          └── q5_cross_school_accuracy.pdf

--------------------------------------------------
Question 6 — Community Detection and Social Drivers
--------------------------------------------------

Script:
  analysis_q6.py

Purpose:
  Investigate which social attributes drive the spontaneous formation of
  network communities in Facebook university networks.

Research logic:
  - Reverse perspective compared to Q5:
      Q5: Can structure predict attributes?
      Q6: Can attributes explain structure?
  - Compare detected communities with true attributes using ARI
    (Adjusted Rand Index).

Algorithms used:
  - Louvain community detection (modularity-based, global)
  - Label Propagation Algorithm (asynchronous, local)

Attributes evaluated:
  - dorm
  - year
  - major
  - gender

Evaluation metric:
  - Adjusted Rand Index (ARI)

Outputs:
  results_q6/
    ├── q6_ari_long.csv
    ├── q6_ari_pivot_mean.csv
    └── figures/
          └── q6_ari_heatmap.pdf (if generated)

--------------------------------------------------
PDF Report
--------------------------------------------------

Homework_Network_Analysis.pdf

Contains:
  - Full written report
  - Methodological explanations
  - Tables and figures imported from results folders
  - Interpretation and discussion for Questions 2–6

--------------------------------------------------
Reproducibility Notes
--------------------------------------------------

- All scripts are independent and can be run separately.
- Each script reads from the data/ folder and writes only to its corresponding
  results_qX/ directory.
- Random seeds are fixed in Q5 and Q6 to ensure reproducibility.

--------------------------------------------------
End of README
--------------------------------------------------
