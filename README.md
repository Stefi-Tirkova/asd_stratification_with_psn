# Stratification of individuals with Autism Spectrum Disorder using Patient Similarity Networks

## Abstract
Autism Spectrum Disorder (ASD) is a complex neurodevelopmental condition that poses challenges in diagnosis and treatment due to its heterogeneity. This study leverages Patient Similarity Networks (PSNs) and community detection algorithms to stratify ASD patients into more homogeneous subgroups using data from the SPARK initiative. By applying Louvain community detection, five distinct ASD subgroups with unique phenotypic profiles were identified. Random Forest classifiers achieved high accuracy in automating subgroup classification. The findings underscore the efficacy of detailed clinical variables over traditional summary scores and demonstrate the potential for personalised treatment, improved diagnostic accuracy, and better clinical trial design. These methodologies can be extended to other complex conditions, paving the way for advancements in personalised medicine and precision health.


<!-- This project contains various experiments and analyses related to community detection and classification using Louvain clustering and Random Forest classifiers. The code is organised into several Jupyter notebooks, each focusing on different aspects of the analysis. -->

## Folder Structure

- `data_prep/`
  - `spark_data_exploration.ipynb`: Some distribution plots and initial exploration.
  - `spark_data_prep.ipynb`: Data filtering, final dataset to work with.
  - `spark_data_prep_summary_scores.ipynb`: Data filtering, saving dataset for ASD individuals with summary scores.

- `rf_classifiers/`
  - `rf_asd_vs_non_asd.ipynb`: Train a Random Forest classifier for ASD vs. non-ASD and save feature importances.
  - `sorted_feature_importances_RF.pkl`: Feature importances used as weights for weighted Hamming similarity.
  - `rf_for_asd_subgroups/`
    - `rf_all_patients_asd_subgroups.ipynb`: RF classifier based on communities derived from all individuals; feature importance saved in `sorted_feature_importances_all_data_multiclass.pkl`.
    - `rf_asd_only.ipynb`: RF classifier based on communities derived from ASD individuals; ; feature importance saved in `sorted_feature_importances_asd_only.pkl`.
    - `rf_asd_only_testing.ipynb`: Predicting ASD subgroups for all unseen ASD individuals in the training and validation of the model above.
    - `all_RFs_importances_plot.ipynb`: Plotting the feature importance of all RF classifiers side by side to aid comparison.

- `psn_sparsification_methods_comparison/`
  - `best_psn_spectral_clustering_hamming_sim.ipynb`: Compare K-nearest neighbors (KNN) and thresholding sparsification methods for building a PSN using Hamming similarity as a patient similarity metric. Different parameters for K (number of neighbors) and t (threshold) are explored and Rand index assessing the split of a spectral clustering of the resulting PSN into ASD and non-ASD nodes is calculated.
  - `best_psn_spectral_clustering_weighted_hamming_sim.ipynb`: Same as above but using weighted Hamming similarity as patient similarity metric.
  - `spectral_clustering_weighted_hamming_sim_results_plots.ipynb`: Plots some of the results for the weighted Hamming similarity across different sample sizes of the PSN.

- `louvain_community_detection/`
  - `louvain_sampling_knn.ipynb`: Performing Louvain clustering on the PSN sparsified using the K-nearest neighbors (KNN) algorithm for all individuals. This includes steps for building the PSN, cleaning the network, and executing Louvain clustering.
  - `louvain_knn_analyse_results.ipynb`: Analyse and visualise the results generated from the file above, including loading the results, calculating metrics, and plotting the clusters.
  - `asd_only_louvain_sampling_knn.ipynb`: Performing Louvain clustering on the PSN sparsified using the K-nearest neighbors (KNN) algorithm for ASD individuals. This includes steps for building the PSN, cleaning the network, and executing Louvain clustering.
  - `asd_only_louvain_knn_analyse_results.ipynb`: Analyse and visualise the results generated from the file above, including loading the results, calculating metrics, and plotting the clusters.
    
    Note: The notebooks in this folder are also utilised to examine the robustness of communities across different subpopulations.


## Dataset
This research project utilises phenotypic data from the SPARK dataset. To ensure data protection and privacy, all personal data used and generated in the project has been excluded from this repository. For more information on how to request access to the dataset, please visit: [SPARK Dataset](https://www.sfari.org/resource/spark/)

## Prerequisites

- Python 3.9
- Jupyter Notebook
- Required Python packages (listed in `requirements.txt`)
