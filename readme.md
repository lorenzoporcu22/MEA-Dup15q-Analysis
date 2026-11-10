
Phenotypic Screening of Dup15q Syndrome in iPSC-Derived Neuronal Networks (HD-MEA)
Overview
This repository contains an advanced, automated MATLAB pipeline designed for the quantitative analysis of High-Density Microelectrode Array (HD-MEA) recordings. The project evaluates the electrophysiological dynamics of human induced pluripotent stem cell (iPSC)-derived excitatory neuronal networks (Ngn2), rigorously comparing a healthy Control group against a Dup15q pathological disease model (N = 3 wells per condition).

The analytical framework bridges macro-scale network dynamics with high-resolution micro-architectural feature extraction, exploring intra-burst structural fragmentation as a potential electrophysiological feature for Dup15q phenotypic characterization.

1. Primary Phenotypic Screening (Macro-Metrics)
A primary comparison across standard electrophysiological descriptors reveals distinct operational characteristics between healthy and pathological networks.

While global baseline activity (Mean Firing Rate) showed no clear separation between Control and Dup15q networks (p = 0.4000), the Network Burst Rate exhibited complete rank separation between the two conditions (p = 0.1000). Among intra-burst metrics, the Percentage of Spikes During Network Bursts also showed complete rank separation (p = 0.1000), whereas Intra-Burst Firing Rate showed no comparable separation (p = 0.7000).


Statistical Foundation (N = 3 Limitation & Complete Rank Separation)
Group comparisons are performed at the well level using a two-sided Mann–Whitney U test (Wilcoxon rank-sum test). With N = 3 wells per group, the total number of possible rank allocations is 20. Consequently, the minimum achievable exact two-sided p-value is:
p_min = 2/20 = 0.1000
Therefore, even complete rank separation between the experimental conditions cannot reach the conventional statistical significance threshold of p < 0.05 with the current sample size.

For selected metrics, including Network Burst Rate, Percentage of Spikes During Network Bursts, and Burst Fragmentation, the observed values showed complete rank separation between Control and Dup15q wells. These findings indicate marked differences in the current dataset, although their statistical significance and reproducibility require further investigation using a larger sample size.

2. Micro-Architecture: Raster & Population IFR Overlay
Because the core phenotypic divergence is hidden within the micro-dynamics of individual events, global averages are insufficient. To visualize this, the pipeline features a dual-axis architecture overlaying single-electrode raster plots with the smoothed population Instantaneous Firing Rate (IFR).

The representative recordings show qualitative differences in the temporal organization of intra-burst activity. Control networks generally display smoother, predominantly single-peaked firing profiles, whereas Dup15q networks show more variable profiles, sometimes characterized by multiple peaks and secondary activity patterns.

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
Averaging fragment counts across network bursts provides a quantitative measure of intra-burst temporal organization. In the current dataset, Control networks displayed predominantly single-peaked profiles, averaging approximately 1 fragment per burst, whereas Dup15q networks showed higher fragment counts, ranging from 7.5 to 12 sub-peaks per burst. These observations showed complete rank separation between the three wells in each condition (p = 0.1000), suggesting that burst fragmentation may represent a promising candidate feature for further investigation in Dup15q neuronal networks.

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

