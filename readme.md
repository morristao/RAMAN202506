# PLS-DA Spectrum Classification with VIP-Based Feature Selection

This repository implements a complete pipeline for multi-class spectral classification of Sudan Red dyes using Partial Least Squares Discriminant Analysis (PLS-DA) combined with Variable Importance in Projection (VIP)-based feature selection. It supports both `.asc` and `.spc` spectrum file formats, and provides cross-validation, hamming accuracy evaluation, and visualization tools.

---

##  Model Overview

This project performs the following tasks:

1. **Preprocessing**: Spectral interpolation and normalization for both wavelength and intensity
2. **PLS-DA Classification**: Using `PLSRegression` + `LinearDiscriminantAnalysis` to project spectra into discriminative space
3. **VIP Feature Selection**: Selects the most informative features using VIP thresholds
4. **Accuracy Evaluation**:
   - **Standard Accuracy** (classification)
   - **Hamming Accuracy** (multi-label or proportional components)
5. **Visualization Outputs**:
   - Accuracy vs VIP Threshold plot
   - VIP-selected feature marker plot (on wavelength axis)
   - 2D PLS-DA category scatterplot

---

##  System Requirements

- **Python**: 3.8+
- **Memory**: ≥4GB (recommended 8GB+ for larger datasets)
- **GPU**: Not required (can run on CPU)

---

##  Installation

We recommend using a virtual environment (e.g., `conda`, `venv`).

```bash
pip install -r requirements.txt
```

Or manually install:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn torch pywt
pip install spectrochempy  # for .spc file support
```

---

##  Data Format & Input

### Supported formats:

- `.asc`: Tab-separated wavelength-intensity format
- `.spc`: Binary spectral format parsed by `spectrochempy`

### File Naming Convention (for automatic label parsing):

```
III+IV(1比1)-xxx.asc   → Sudan Red III:50%, IV:50%
1+2(33%毑66%)-xxx.spc → Sudan Red I:33%, II:66%
```

Labels will be auto-parsed into 4-component proportion vectors.

---

##  Inputs & Outputs

### Input:

- Spectrum files placed inside folders like:
  - `remix_data/`, `remix_data_2/`, `remix_data_3/`
- Parameters like VIP threshold range, max PLS components

### Output:

- `PLS-DA Spectrum Categorization Result.png`
- `VIP Threshold vs Accuracy.png`
- `Selected VIP Features Plot.png`
- Console outputs for accuracy and hamming scores

---

##  Usage Steps

### 1. Clone and setup

```bash
git clone https://github.com/your-username/sudan-red-spectrum.git
cd sudan-red-spectrum
pip install -r requirements.txt
```

### 2. Prepare spectral data

Place `.asc` or `.spc` files into:

```text
remix_data/
remix_data_2/
remix_data_3/
```

### 3. Run the notebook

```bash
jupyter notebook Project_handout20250616.ipynb
```

Or convert to script:

```bash
jupyter nbconvert --to script Project_handout20250616.ipynb
python Project_handout20250616.py
```

---

##  Evaluation Metrics

- **Accuracy**: Standard classification accuracy
- **Hamming Accuracy**: Element-wise correctness for multi-label proportions
- **VIP Feature Count**: Number of selected features at each threshold

---

##  Project Structure

```text
.
├── Project_handout20250616.ipynb     # Main notebook
├── SpectrumDataset.py                # Spectrum dataset class
├── utils.py                          # Utility functions (VIP, hamming)
├── /remix_data                       # Raw spectrum files (.asc / .spc)
├── /output                           # Plots and results
└── README.md
```

---

##  Resources

- [scikit-learn: PLSRegression](https://scikit-learn.org/stable/modules/generated/sklearn.cross_decomposition.PLSRegression.html)
- [SpectroChemPy](https://www.spectrochempy.fr/)
- [Hamming Loss in scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.hamming_loss.html)

---

##  Contact

> Maintainer: **Your Name**\
> Email: `your_email@example.com`

For issues or suggestions, please open a [GitHub Issue](https://github.com/your-username/sudan-red-spectrum/issues).

