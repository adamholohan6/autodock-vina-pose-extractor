# AutoDock Vina High-Throughput Pose Extractor

## 📌 Executive Overview
AutoDock Vina natively outputs structural predictions into a single, multi-model `.pdbqt` file, creating a data bottleneck for downstream analytical workflows and molecular dynamics simulations. 

**This repository documents a lightweight Python pipeline** developed to automate structural pose extraction and safeguard data integrity. Originally inspired by the data workflow from my master's thesis.

### Key Project Pillars
* **High-Throughput Automation:** Native Python-based parsing that operates entirely in memory, bypassing external bioinformatics dependencies.
* **Data Integrity Framework:** Born out of a real-world post-submission data audit to eliminate manual transcription risks and enforce reproducibility.
* **Quantitative Upskilling Roadmap:** A multi-phase plan to leverage this data workflow for expanded virtual library generation, R-based physicochemical screening, and exploratory data analysis.

## ⚙️ Core Features
* **High-Throughput Batching:** Automatically processes all raw docking outputs with a single command.
* **Zero External Dependencies:** Operates using native Python libraries only, bypassing external package managers.
* **Automated Data Validation:** Extracts `REMARK VINA RESULT` energy scores and compiles them into a quality-sorted `.csv` summary sheet, eliminating manual data-entry risks.
* **Cross-Platform Compatibility:** Works seamlessly on Linux, macOS, and Windows.

## 🚀 Installation & Quick Start

### Requirements
- **Python 3.6+** (Python 2 is no longer supported)

### Basic Usage

**Single file extraction:**
```bash
python split_poses_2.py your_docking_output.pdbqt
```

**Specify custom output directory:**
```bash
python split_poses_2.py your_docking_output.pdbqt -o ./my_poses
```

**View help:**
```bash
python split_poses_2.py -h
```

### Example Workflow

```bash
# Extract poses from a docking run
python split_poses_2.py redock-talo-10.pdbqt -o ./extracted_poses

# Output:
# [SUCCESS] Pipeline Execution Complete.
# -> Extracted 3 individual poses into: 'extracted_poses'
# -> Automated data validation sheet generated: 'extracted_poses/redock-talo-10_docking_summary.csv'
```

This generates:
- `redock-talo-10_pose_1_-8.2kcal.pdb`
- `redock-talo-10_pose_2_-8.1kcal.pdb`
- `redock-talo-10_pose_3_-8.0kcal.pdb`
- `redock-talo-10_docking_summary.csv` (validation log)

## 📊 Data Integrity & Quality Assurance

The motivation for automating this workflow came directly from a common research headache. Right after submitting my master's thesis and just before a poster presentation, I noticed a manual transcription error that could have compromised my results.

Because managing large sets of computational outputs manually makes those kinds of slip-ups easy, this script was engineered as a permanent solution. It establishes a programmatic validation layer that ensures:
- **Structural data** is never decoupled from its corresponding **binding affinity**
- **Filenames** encode binding affinity directly, preventing mix-ups
- **CSV summary** provides an auditable trail of all extracted poses

### Data Integrity Example

If a target ligand yields competitive binding affinities ranging from **-8.0 to -8.2 kcal/mol**, those scores are:
1. Extracted directly from the PDBQT file
2. Embedded in output filenames
3. Logged in a CSV with full traceability

**Input:** `redock-talo-10.pdbqt` (Multi-model file)

**Output:**
1. `redock-talo-10_pose_1_-8.2kcal.pdb`
2. `redock-talo-10_pose_2_-8.1kcal.pdb`
3. `redock-talo-10_pose_3_-8.0kcal.pdb`
4. `redock-talo-10_docking_summary.csv` (Quality-sorted validation log)

## 📁 Project Structure

```
autodock-vina-pose-extractor/
├── split_poses_2.py              # Main extraction script
├── README.md                      # This file
├── requirements.txt               # Python dependencies (none required)
└── extracted_poses/               # Output directory (auto-created)
    ├── *.pdb                      # Individual pose files
    └── *_docking_summary.csv      # Validation summary
```

## 🔧 Troubleshooting

### Issue: "PDBQT file not found"
**Solution:** Verify the file path is correct and the file exists.
```bash
# Check file exists
ls -la your_file.pdbqt

# Use absolute path if needed
python split_poses_2.py /full/path/to/file.pdbqt
```

### Issue: "Permission denied" on output directory
**Solution:** Ensure you have write permissions to the target directory.
```bash
# Create directory with proper permissions
mkdir -p extracted_poses
chmod 755 extracted_poses
```

### Issue: Binding affinity shows "0.0" for all poses
**Solution:** Verify your PDBQT file contains `REMARK VINA RESULT` lines with properly formatted energy scores.
```bash
# Check file format
grep "REMARK VINA RESULT" your_file.pdbqt
```

### Issue: Script runs but generates empty CSV
**Solution:** The input file may not contain `ATOM` or `HETATM` records. Verify the PDBQT file is properly formatted.

## 🔬 Development Roadmap

- [x] **Phase 1: Workflow Automation & Core Binding Validation** (Completed)
  * Automated parsing of multi-model Vina outputs, format standardization, and data-integrity logging
  * Python 3.6+ modernization
  * Command-line interface with argparse

- [ ] **Phase 2: Virtual Library Expansion & R-Based Physicochemical Screening** (Planned)
  * Generating expanded virtual library of structural variations
  * R-based physicochemical descriptor calculations
  * Lipinski's Rule of Five filtering

- [ ] **Phase 3: Exploratory Data Analysis & ADMET Filtering** (Roadmap)
  * R-based statistical analysis (PCA, clustering)
  * In silico toxicity screening
  * Advanced visualization dashboards

## 📄 License

This project is provided as-is for research and educational purposes.

## 🤝 Contributing

Contributions are welcome! Please feel free to:
- Report bugs or issues
- Suggest improvements
- Submit pull requests with enhancements

## 📧 Questions?

For questions or issues, please open a GitHub issue in this repository.
