# AutoDock Vina High-Throughput Pose Extractor

## 📌 Overview
AutoDock Vina natively outputs structural predictions into a single, multi-model `.pdbqt` file. This creates a data bottleneck, as downstream analytical servers, molecular dynamics simulations, and standard visualization tools require standalone, single-conformation files.

This lightweight Python pipeline automates the extraction process. It natively parses batch directories of raw multi-model files, converts them into universally compliant `.pdb` formats, and safeguards data integrity by binding thermodynamic metadata directly to both the output filenames and a master validation spreadsheet.

## ⚙️ Core Features
* **High-Throughput Batching:** Automatically scans directories and processes all raw docking outputs with a single command.
* **Zero Binary Dependencies:** Operates entirely within native Python memory using string manipulation, bypassing the need for external package managers or compiled bioinformatics tools.
* **Automated Data Validation:** Extracts `REMARK VINA RESULT` energy scores and compiles them into a quality-sorted `.csv` summary sheet, eliminating manual data-entry risks.
* **Environment Robustness:** Features conditional syntax routing to ensure seamless dual-compatibility across legacy Python 2 and modern Python 3 architectures.

## 📊 Data Integrity Example
The script prevents the decoupling of structural data from performance metrics. For example, if a target ligand (e.g., a taloside derivative) yields highly competitive binding affinities ranging from **-8.0 to -8.2 kcal/mol**, those exact scores are permanently stamped into the isolated structural files:

**Input:** `redock-talo-10.pdbqt` (Multi-model file)
**Output:** 1. `redock-talo-10_pose_1_-8.2kcal.pdb`
2. `redock-talo-10_pose_2_-8.1kcal.pdb`
3. `redock-talo-10_pose_3_-8.0kcal.pdb`
4. `master_screening_summary.csv` (Quality-sorted validation log)

## 🚀 Future Development Roadmap
- [ ] Integrate quantitative QSAR descriptor modeling in R.
- [ ] Develop a mechanism-based, two-compartment PK/PD model to translate thermodynamic binding affinity ($K_d$) into simulated plasma concentration profiles.