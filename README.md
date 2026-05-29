# AutoDock Vina High-Throughput Pose Extractor

## 📌 Executive Overview
AutoDock Vina natively outputs structural predictions into a single, multi-model `.pdbqt` file, creating a data bottleneck for downstream analytical workflows and molecular dynamics simulations. 

**This repository documents a lightweight Python pipeline** developed to automate structural pose extraction and safeguard data integrity. Originally inspired by the data workflow from my master's research on synthetic taloside-triazole derivatives against Galectin-3 at the University of Galway, this utility eliminates manual file-handling errors by programmatically binding thermodynamic metadata directly to both output files and master evaluation logs.

### Key Project Pillars
* **High-Throughput Automation:** Native Python-based parsing that operates entirely in memory, bypassing external bioinformatics dependencies.
* **Data Integrity Framework:** Born out of a real-world post-submission data audit to eliminate manual transcription risks and enforce reproducibility.
* **Quantitative Upskilling Roadmap:** A multi-phase plan to leverage this data workflow for expanded virtual library generation, R-based physicochemical screening, and exploratory data analysis (PCA).

## ⚙️ Core Features
* **High-Throughput Batching:** Automatically scans directories and processes all raw docking outputs with a single command.
* **Zero Binary Dependencies:** Operates using native Python string manipulation, bypassing the need for external package managers or compiled tools.
* **Automated Data Validation:** Extracts `REMARK VINA RESULT` energy scores and compiles them into a quality-sorted `.csv` summary sheet, eliminating manual data-entry risks.
* **Environment Robustness:** Features conditional syntax routing to ensure seamless dual-compatibility across legacy Python 2 and modern Python 3 architectures.

## 🔍 Data Integrity & Quality Assurance
The motivation for automating this workflow came directly from a common research headache. Right after submitting my master's thesis and just before a poster presentation, I noticed a manual transcription error in my data summary (specifically affecting the meta-substituted taloside series in Figure 4c). 

Because managing large sets of computational outputs manually makes those kinds of slip-ups easy, this script was engineered as a permanent solution. It establishes a programmatic validation layer to ensure raw simulation outputs and reported narratives always align perfectly.

## 📊 Data Integrity Example
The script prevents the decoupling of structural data from performance metrics. For example, if a target ligand yields competitive binding affinities ranging from **-8.0 to -8.2 kcal/mol**, those exact scores are permanently stamped into the isolated structural files:

* **Input:** `redock-talo-10.pdbqt` (Multi-model file)
* **Output:** 1. `redock-talo-10_pose_1_-8.2kcal.pdb`
  2. `redock-talo-10_pose_2_-8.1kcal.pdb`
  3. `redock-talo-10_pose_3_-8.0kcal.pdb`
  4. `master_screening_summary.csv` (Quality-sorted validation log)

## 🚀 Future Development Roadmap
- [x] **Phase 1: Workflow Automation & Core Binding Validation** (Completed)
  * Automated parsing of multi-model Vina outputs, format standardization, and data-integrity logging to eliminate manual transcription risks.
- [ ] **Phase 2: Virtual Library Expansion & R-Based Physicochemical Screening** (Planned)
  * Generating an expanded virtual library of 50–100 structural variations of the meta-substituted talosides, utilizing R to calculate physicochemical descriptors and apply Lipinski’s Rule of 5 filters.
- [ ] **Phase 3: Exploratory Data Analysis & ADMET Filtering** (Roadmap)
  * Utilizing R for statistical analysis (such as Principal Component Analysis - PCA) to map the chemical space of the generated library, combined with early-stage in silico toxicity screening.
