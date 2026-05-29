# AutoDock Vina High-Throughput Pose Extractor

## 📌 Executive Overview
AutoDock Vina natively outputs structural predictions into a single, multi-model `.pdbqt` file, creating a significant bottleneck for downstream analytical workflows and molecular dynamics simulations. 

**This repository documents a custom Python-based processing pipeline** developed for the structural optimization of synthetic taloside-triazole derivatives against the Galectin-3 Carbohydrate Recognition Domain. Beyond simple file parsing, this project serves as a central hub for an ongoing preclinical research workflow, prioritizing **data integrity, translational pharmacometrics, and systematic lead optimization.**

### Key Project Pillars
* **High-Throughput Automation:** Native Python-based parsing that bypasses the need for external bioinformatics dependencies.
* **Rigorous Data Integrity:** Includes a post-thesis audit layer ensuring absolute consistency between master thermodynamic datasets and reported results—a core requirement for regulatory and clinical data compliance.
* **Strategic R&D Roadmap:** An integrated, multi-phase pipeline that maps the progression from static empirical docking to machine-learning-based QSAR and translational PK/PD pharmacometrics.

## ⚙️ Core Features
* **High-Throughput Batching:** Automatically scans directories and processes all raw docking outputs with a single command.
* **Zero Binary Dependencies:** Operates entirely within native Python memory using string manipulation, bypassing the need for external package managers or compiled bioinformatics tools.
* **Automated Data Validation:** Extracts `REMARK VINA RESULT` energy scores and compiles them into a quality-sorted `.csv` summary sheet, eliminating manual data-entry risks.
* **Environment Robustness:** Features conditional syntax routing to ensure seamless dual-compatibility across legacy Python 2 and modern Python 3 architectures.

## 🔍 Data Integrity & Quality Assurance
This pipeline includes a post-thesis audit layer designed to ensure consistency between master thermodynamic datasets and reported narratives. During this audit, a transcription discrepancy was identified and corrected within the meta-substituted taloside series (Figure 4c), ensuring that the reported binding affinities align with the raw computational outputs. This commitment to data provenance is a core tenet of the current research workflow.

## 📊 Data Integrity Example
The script prevents the decoupling of structural data from performance metrics. For example, if a target ligand yields highly competitive binding affinities ranging from **-8.0 to -8.2 kcal/mol**, those exact scores are permanently stamped into the isolated structural files:

**Input:** `redock-talo-10.pdbqt` (Multi-model file)
**Output:** 1. `redock-talo-10_pose_1_-8.2kcal.pdb`
2. `redock-talo-10_pose_2_-8.1kcal.pdb`
3. `redock-talo-10_pose_3_-8.0kcal.pdb`
4. `master_screening_summary.csv` (Quality-sorted validation log)

## 🚀 Future Development Roadmap
- [x] **Phase 1: Structural Docking & Data Audit** (Completed: Automated pipeline established; Figure 4c integrity verified).
- [ ] **Phase 2: Quantitative QSAR Descriptor Modeling** (Planned: Integration of R-based machine learning models to correlate structural descriptors with binding affinity).
- [ ] **Phase 3: Systems-Level PK/PD Integration** (Planned: Development of a mechanism-based, two-compartment model via `deSolve` to translate $K_d$ values into longitudinal plasma concentration profiles).
