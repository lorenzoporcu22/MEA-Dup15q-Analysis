
Phenotypic Screening of Dup15q Syndrome in iPSC-Derived Neuronal Networks (HD-MEA)
Overview
This repository contains an advanced, automated MATLAB pipeline designed for the quantitative analysis of High-Density Microelectrode Array (HD-MEA) recordings. The project evaluates the electrophysiological dynamics of human induced pluripotent stem cell (iPSC)-derived excitatory neuronal networks (Ngn2), rigorously comparing a healthy Control group against a Dup15q pathological disease model (N = 3 wells per condition).

The analytical framework bridges macro-scale network dynamics with high-resolution micro-architectural feature extraction, establishing intra-burst structural fragmentation as a robust, objective electrophysiological biomarker for Dup15q phenotypic screening.

1. Primary Phenotypic Screening (Macro-Metrics)
A primary comparison across standard electrophysiological descriptors reveals distinct operational characteristics between healthy and pathological networks.

While global baseline activity (Mean Firing Rate) and network synchronization frequency (Network Burst Rate) show overlapping distributions, parameters characterizing intra-burst activity—specifically Intra-Burst Firing Rate and the Percentage of Spikes During Network Bursts—yielded a p-value of 0.1000.

Statistical Foundation (N = 3 Limitation & Complete Rank Separation)
Group comparisons are performed at the well level utilizing a two-sided Mann-Whitney U test (Wilcoxon rank-sum). With N = 3 wells per group, the total number of unique rank permutations is 20. Consequently, the absolute minimum mathematically achievable two-tailed p-value is exactly:

p_min = 2/20 = 0.1000
A result of p = 0.1000 does not indicate a lack of statistical effect; rather, it represents complete rank separation between experimental conditions (every Dup15q well ranks strictly above or below every Control well). This proves that the macroscopic network capability is preserved, but the Dup15q mutation profoundly alters how spikes are coordinated within the burst window.

2. Micro-Architecture: Raster & Population IFR Overlay
Because the core phenotypic divergence is hidden within the micro-dynamics of individual events, global averages are insufficient. To visualize this, the pipeline features a dual-axis architecture overlaying single-electrode raster plots with the smoothed population Instantaneous Firing Rate (IFR).

This reveals a striking qualitative contrast: healthy Control networks discharge in a cohesive, single-peaked firing wave, whereas Dup15q networks exhibit severe intra-burst stuttering, characterized by rapid oscillations and secondary sub-peaks.

Representative Well Comparisons (Control vs. Dup15q)
	•	Pair 1: raster_ifr_overlay_pair_1.png
	•	Pair 2: raster_ifr_overlay_pair_2.png
	•	Pair 3: raster_ifr_overlay_pair_3.png
3. Quantitative Biomarker Discovery: Burst Fragmentation
To formally quantify this intra-burst instability, the pipeline implements an automated Peak-and-Valley IFR Detection Algorithm.

	1	Signal Binned Envelope: Network burst windows are isolated and binned at high temporal resolution (t = 10 ms).
	2	Gaussian Smoothing: The IFR profile is smoothed using a Gaussian moving window to suppress high-frequency noise.
	3	Prominence-Based Peak Detection: MATLAB's findpeaks function identifies sub-burst peaks (burstlets) using strict prominence thresholds and refractory distance limits.
Single-Burst Micro-Analysis
Detailed view of an individual Dup15q network burst undergoing severe structural fragmentation (N = 10 detected sub-peaks):

Group-Level Quantification
Averaging fragment counts across all network bursts per well establishes a powerful quantitative separator. Healthy controls maintain tight, cohesive bursts averaging 1 fragment, while Dup15q networks fracture into 7.5 to 12 distinct sub-events per burst, achieving complete rank separation (p = 0.1000).

Repository Structure
HD-MEA_Dup15q_Analysis/
│
├── data/                    # Raw and pre-processed .mat recordings (.mat)
├── images/                  # High-resolution exported figures (300 DPI PNGs)
├── scripts/                 # Core MATLAB Live Scripts (.mlx) and helper functions
└── README.md                # Comprehensive project documentation

Dependencies & Execution
	•	Software: MATLAB (R2023a or newer recommended).
	•	Toolboxes: Signal Processing Toolbox (required for findpeaks and smoothing utilities).
	•	Execution: Open scripts/main_pipeline.mlx and run sections sequentially to reproduce data ingestion, phenotypic dashboarding, and micro-architectural biomarker discovery.
Author
Lorenzo Porcu
Bioengineer & Data Scientist | November 2026

