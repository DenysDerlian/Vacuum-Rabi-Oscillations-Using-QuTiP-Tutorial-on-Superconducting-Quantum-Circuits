# Vacuum Rabi Oscillations Using QuTiP: Computational Supplement

**Associated Publication:** *Tutorial on Superconducting Quantum Circuits: From Basics to Applications*

---

## Purpose

This repository contains the computational supplement for the article "*Tutorial on Superconducting Quantum Circuits: From Basics to Applications*". The Jupyter notebook provides detailed implementations and extended analysis of vacuum Rabi oscillations in transmon-resonator systems, going beyond the theoretical treatment presented in the main paper.

**Intended Audience:**
- Researchers seeking to reproduce and verify computational results
- Reproducibility reviewers validating the manuscript
- Graduate students learning superconducting quantum circuit simulation
- Scientists extending the work with modified parameters or scenarios

---

## Repository Contents

```
.
├── Vacuum_Rabi_Oscillations_Using_QTip.ipynb  # Main computational notebook
├── README.md                                   # This file
├── requirements.txt                            # Python dependencies with pinned versions
├── environment.yml                             # Conda environment specification (optional)
└── images/                                     # Generated figures (created on first run)
```

---

## Prerequisites

### System Requirements
- **Operating System:** Linux, macOS, or Windows
- **Python Version:** 3.8 or higher (tested with Python 3.10)
- **RAM:** Minimum 4 GB (8 GB recommended for high-resolution vacuum Rabi graphs)
- **Disk Space:** ~500 MB for dependencies

### Required Knowledge
- Basic quantum mechanics (two-level systems, harmonic oscillators)
- Familiarity with Python and Jupyter notebooks
- Understanding of open quantum systems (helpful but not required)

---

## Quick Start

### Option 1: Using pip (Recommended)

1. **Clone or download this repository:**
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter:**
   ```bash
   jupyter notebook Vacuum_Rabi_Oscillations_Using_QTip.ipynb
   ```

5. **Run cells sequentially** from top to bottom (Shift+Enter for each cell)

### Option 2: Using Conda

1. **Create environment from file:**
   ```bash
   conda env create -f environment.yml
   conda activate rabi-oscillations
   ```

2. **Launch Jupyter:**
   ```bash
   jupyter notebook Vacuum_Rabi_Oscillations_Using_QTip.ipynb
   ```

---

## Expected Outputs

### Computational Results

The notebook generates the following analyses:

1. **System Evolution Scenarios:**
   - No resonance (detuned system)
   - Different frequencies (large detuning)
   - No dissipative interactions (ideal, closed system)
   - Dissipative interactions (open system with decay)
   - Frequency detuning dynamics (Heaviside and Gaussian pulses)
   - Non-zero temperature effects

2. **Comparison of Methods:**
   - Full Hamiltonian (no approximations)
   - Rotating Wave Approximation (RWA)
   - Drive-induced dynamics (realistic microwave pulses)

3. **Vacuum Rabi Graph:**
   - 2D map showing excitation probability vs. detuning and interaction time
   - Demonstrates resonance condition and coupling strength effects
   - **Note:** High-resolution version (100×100 grid) takes ~2-3 hours

### Generated Figures

All figures are saved to `./images/` as PDF files with publication-quality formatting:
- `No resonance.pdf`
- `Different frequencies.pdf`
- `No dissipative interactions.pdf`
- `Dissipative interactions.pdf`
- `Frequency detuning - Heaviside.pdf`
- `Frequency detuning - Gaussian.pdf`
- `Vacuum Rabi Graph.pdf`

### Typical Runtime

- **Full notebook:** 5-10 minutes (with default resolution)
- **Vacuum Rabi Graph (high-res):** 2-3 hours (can be skipped or run at lower resolution)

---

## Reproducibility Notes

### Deterministic Results
All simulations are deterministic (no random sampling). Results should be identical across different machines with the same software versions.

### Version Pinning
The `requirements.txt` file pins exact versions of all dependencies to ensure reproducibility. If you encounter compatibility issues with your system, you can relax version constraints, but results may differ slightly.

### Numerical Precision
- QuTiP uses sparse matrix methods for efficiency
- Truncation of Hilbert space: N=10 Fock states (sufficient for weak excitations)
- Time discretization: 256 points (adequate for capturing oscillations)

### Figures and Data
The notebook generates figures matching those in the manuscript. Minor differences may arise from:
- Matplotlib version differences (use pinned version for exact reproduction)
- Display backend settings (use `Agg` backend for consistency)

---

## Customization and Extension

### Modifying Parameters

Key parameters can be adjusted in the "Initial States" section:

```python
N = 10                    # Fock space dimension
w_R = 7.0 * 2 * np.pi    # Cavity frequency (GHz)
w_T = 5.0 * 2 * np.pi    # Qubit frequency (GHz)
g = 0.20 * 2 * np.pi     # Coupling strength (GHz)
kappa = 2 * np.pi * 0.016  # Cavity decay rate
gamma = 2 * np.pi * 0.050  # Qubit decay rate
```

### Adding New Scenarios

The notebook structure makes it easy to add new analyses:
1. Define new Hamiltonian parameters using `hamiltonian_gen()`
2. Solve dynamics with `mesolve()` or `hamiltonian_Drive_solver()`
3. Visualize results with `plot_prob()`

### Performance Optimization

For faster execution:
- Reduce time resolution: `t = np.linspace(0, 10, 128)`
- Lower vacuum Rabi graph resolution: `resolution = 50`
- Reduce Fock space: `N = 5` (check convergence!)

---

## Citation

If you use this code in your research, please cite the associated paper:

```bibtex
@article{Brito2025SuperconductingCircuits,
  title={Tutorial on Superconducting Quantum Circuits: From Basics to Applications},
  author={Brito, Denys Derlian Carvalho and Valadares, Fernando and Chaves, Andr{\'e} Jorge Carvalho},
  journal={Brazilian Journal of Physics},
  year={2025},
  note={Special Issue: 100 years of Quantum Mechanics},
  doi={[To be assigned]}
}
```

For the computational supplement specifically:

```bibtex
@misc{Brito2025ComputationalSupplement,
  title={Vacuum Rabi Oscillations Using QuTiP: Computational Supplement},
  author={Brito, Denys Derlian Carvalho and Valadares, Fernando and Chaves, Andr{\'e} Jorge Carvalho},
  year={2025},
  howpublished={\url{[Repository URL]}},
  note={Computational supplement to: Tutorial on Superconducting Quantum Circuits}
}
```

---

## Troubleshooting

### Common Issues

**Problem:** `ModuleNotFoundError: No module named 'qutip'`
- **Solution:** Ensure you've activated the virtual environment and run `pip install -r requirements.txt`

**Problem:** Slow execution or memory errors
- **Solution:** Reduce parameters (N, time points, resolution) as described in "Performance Optimization"

**Problem:** Figures not saving
- **Solution:** The `./images/` directory is created automatically. Check write permissions.

**Problem:** Different results than expected
- **Solution:** Verify you're using the exact package versions in `requirements.txt`

### Getting Help

For questions or issues:
1. Check the inline documentation and comments in the notebook
2. Review the associated paper for theoretical background
3. Open an issue on the repository (if applicable)
4. Contact the authors (email addresses in the paper)

---

## License

[Specify license, e.g., MIT, CC-BY-4.0, etc.]

This code is provided as-is for academic and educational purposes. If you modify or extend this work, please acknowledge the original source.

---

## Acknowledgments

This work uses the QuTiP (Quantum Toolbox in Python) library:

> J. R. Johansson, P. D. Nation, and F. Nori: "QuTiP: An open-source Python framework for the dynamics of open quantum systems", *Comp. Phys. Comm.* **183**, 1760 (2012).

> J. R. Johansson, P. D. Nation, and F. Nori: "QuTiP 2: A Python framework for the dynamics of open quantum systems", *Comp. Phys. Comm.* **184**, 1234 (2013).

---

## Contact

**Denys Derlian Carvalho Brito**  
Instituto Tecnológico de Aeronáutica  
Email: derlian@ita.com  
ORCID: [0009-0007-1669-0340](https://orcid.org/0009-0007-1669-0340)

**Fernando Valadares**  
Centre for Quantum Technologies, National University of Singapore  
Email: fernando.valadares@u.nus.edu  
ORCID: [0000-0002-7961-2215](https://orcid.org/0000-0002-7961-2215)

**André Jorge Carvalho Chaves (Corresponding Author)**  
Instituto Tecnológico de Aeronáutica  
Email: andrejck@ita.br  
ORCID: [0000-0003-1381-8568](https://orcid.org/0000-0003-1381-8568)

---

*Last updated: October 23, 2025*
