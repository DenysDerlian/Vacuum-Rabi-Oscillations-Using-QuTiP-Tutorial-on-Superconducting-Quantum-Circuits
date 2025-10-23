# Contributing to Vacuum Rabi Oscillations Computational Supplement

Thank you for your interest in contributing to this computational supplement! This document provides guidelines for contributing improvements, bug fixes, or extensions.

---

## Types of Contributions

We welcome several types of contributions:

### 1. Bug Reports
If you find a bug or unexpected behavior:
- Check if the issue already exists in the Issues section
- Provide a minimal reproducible example
- Include your Python version, OS, and package versions
- Describe expected vs. actual behavior

### 2. Bug Fixes
- Reference the issue number in your pull request
- Include tests or verification that the fix works
- Update documentation if needed

### 3. Documentation Improvements
- Clarify existing explanations
- Fix typos or formatting issues
- Add references or citations
- Improve code comments

### 4. New Features or Extensions
- Discuss proposed changes in an issue first
- Ensure compatibility with existing code
- Follow the existing code style
- Document new functionality thoroughly

---

## Development Setup

1. **Fork the repository** on GitHub

2. **Clone your fork:**
   ```bash
   git clone https://github.com/your-username/repository-name.git
   cd repository-name
   ```

3. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

4. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

5. **Create a branch for your changes:**
   ```bash
   git checkout -b feature/your-feature-name
   ```

---

## Code Style Guidelines

### Python Code
- Follow PEP 8 style guidelines
- Use type hints for function signatures
- Include docstrings for all functions (NumPy/Google style)
- Keep lines under 100 characters when possible
- Use meaningful variable names

### Jupyter Notebooks
- Include markdown cells explaining each section
- Add comments for complex physics or mathematics
- Keep code cells focused (one concept per cell)
- Run "Restart & Run All" before committing

### Documentation
- Use clear, concise language
- Explain physics concepts for educational purposes
- Include units for all physical quantities
- Cite relevant papers or resources

---

## Commit Message Format

Use clear, descriptive commit messages:

```
Short summary (50 chars or less)

More detailed explanation if needed. Wrap at 72 characters.
Explain what changed and why, not how (code shows how).

- Bullet points are okay
- Reference issues: Fixes #123

Signed-off-by: Your Name <your.email@example.com>
```

Examples:
- `Fix: Correct cavity decay rate calculation`
- `Docs: Add explanation of RWA approximation`
- `Feature: Implement dispersive regime simulation`

---

## Testing

Before submitting a pull request:

1. **Run all notebook cells:**
   - Restart kernel and run all cells
   - Verify no errors occur
   - Check that outputs are reasonable

2. **Verify reproducibility:**
   - Clear outputs: `jupyter nbconvert --clear-output --inplace notebook.ipynb`
   - Re-run completely
   - Compare results with previous version

3. **Check dependencies:**
   - Ensure new code doesn't require additional packages
   - If new packages needed, update `requirements.txt` and `environment.yml`

---

## Pull Request Process

1. **Update documentation:**
   - Add/update docstrings for modified functions
   - Update README.md if functionality changed
   - Document new parameters or behavior

2. **Reference issues:**
   - Link to relevant issues in PR description
   - Use keywords: "Fixes #123" or "Closes #123"

3. **Describe changes:**
   - What was changed and why
   - How to test the changes
   - Any breaking changes or compatibility notes

4. **Wait for review:**
   - Maintainers will review your PR
   - Address any requested changes
   - Once approved, your PR will be merged

---

## Scientific Contributions

### Adding New Simulations

If you want to add new physical scenarios:

1. **Follow existing structure:**
   - Configuration cell explaining the scenario
   - Hamiltonian setup
   - Solve dynamics
   - Visualization with `plot_prob()`

2. **Document physics:**
   - Explain the physical situation
   - State expected behavior
   - Provide relevant equations

3. **Validate results:**
   - Compare with analytical solutions (if available)
   - Check limiting cases
   - Verify energy conservation (where applicable)

### Parameter Modifications

When suggesting new parameter regimes:

1. **Physical justification:**
   - Cite experimental papers using similar parameters
   - Explain why these parameters are interesting

2. **Check validity:**
   - Verify truncation is adequate (N large enough)
   - Ensure numerical stability
   - Check that approximations still hold

---

## Code of Conduct

### Our Standards

- Be respectful and inclusive
- Welcome newcomers and learners
- Provide constructive feedback
- Focus on scientific accuracy
- Give credit where due

### Unacceptable Behavior

- Harassment or discriminatory language
- Personal attacks
- Publishing others' private information
- Plagiarism or uncredited copying

---

## Attribution

Contributors will be acknowledged in:
- README.md (Contributors section)
- Release notes
- Zenodo/publication acknowledgments (for significant contributions)

Please add yourself to the contributors list in your first PR:

```markdown
## Contributors

- [Your Name](https://github.com/your-username) - [Brief contribution]
```

---

## Questions?

If you have questions about contributing:
- Open an issue labeled "question"
- Email the maintainers (see README.md)
- Check existing issues and pull requests

---

## License

By contributing, you agree that your contributions will be licensed under the same license as the original project (MIT License).

---

Thank you for helping improve this computational supplement! Your contributions make science more reproducible and accessible.
