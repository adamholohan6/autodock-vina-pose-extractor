# Contributing to AutoDock Vina Pose Extractor

Thank you for your interest in contributing! This document provides guidelines for contributing to the project.

## How to Contribute

### Reporting Bugs
1. Check existing issues to avoid duplicates
2. Provide a clear description of the bug
3. Include steps to reproduce
4. Attach example PDBQT files or error messages if possible

### Suggesting Enhancements
1. Use GitHub Issues to propose new features
2. Explain the use case and expected behavior
3. Include examples or mockups if applicable

### Submitting Pull Requests
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Follow PEP 8 style guidelines
4. Test your changes thoroughly
5. Commit with clear messages
6. Push to your fork
7. Open a pull request with a clear description

## Code Standards

- **Python Version:** 3.6+
- **Style:** PEP 8
- **Documentation:** Docstrings for all functions
- **Testing:** Include examples of your changes

## Development Setup

```bash
# Clone the repository
git clone https://github.com/adamholohan6/autodock-vina-pose-extractor.git
cd autodock-vina-pose-extractor

# Make changes and test
python split_poses_2.py test_file.pdbqt -o test_output
```

## Questions?

Feel free to open an issue or discussion for questions or ideas!
