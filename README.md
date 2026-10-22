# Min-Max Normalization and PCA Workshop

**Team 6 - Jasper Lim**

## Challenge summary

This completed workshop uses the housing dataset in `data/housing_data.csv` to demonstrate manual Min-Max normalization and Principal Component Analysis (PCA). The notebook normalizes every numeric field while excluding the `House_ID` identifier, handles constant-valued columns safely, and uses the normalized housing features (excluding `Price`) as PCA inputs. `Price` is kept separate as the target for a post-PCA correlation check.

The challenge asks how much variance each principal component captures, how the original features contribute to PC1 and PC2, and whether the components with the most variance also relate to `Price`. On this dataset, four components are needed to reach 90% cumulative explained variance (94.86% total). PC1 is dominated by `Num_Bathrooms`, PC2 by `Num_Bedrooms`, and PC3 has the largest absolute correlation with `Price` (about -0.032) - a negligible linear relationship. The notebook includes graphs for cumulative variance, feature loadings, and component-to-price correlations.

## Setup

1. Install Python 3.11 or later.
2. From the repository root, create and activate a virtual environment in PowerShell:

   ```powershell
   py -3.11 -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

3. Install the pinned dependencies:

   ```powershell
   .\.venv\Scripts\python.exe -m pip install --upgrade pip
   .\.venv\Scripts\python.exe -m pip install -r requirements.txt
   ```

4. In VS Code, install/enable the Python and Jupyter extensions, open this repository, and select the `.venv` Python interpreter as the notebook kernel.

## How to run

1. Open [`MinMax_Normalization_Workshop.ipynb`](./MinMax_Normalization_Workshop.ipynb) in VS Code.
2. Select the `.venv` kernel if prompted.
3. Choose **Run All**. The dataset is loaded from the relative path `data/housing_data.csv`; run the notebook with the repository root as the working folder.

The notebook contains the complete normalization implementation, PCA analysis, written challenge findings, three talking points for each topic, and the PCA visualization section. Re-run all cells after changing the dataset so the displayed findings and graphs are refreshed.

## Main takeaways

- Min-Max scaling places numeric fields on a comparable 0-1 range; it does not make every feature equally informative or protect against outliers.
- PCA is unsupervised: components maximize feature variance, not predictive power for `Price`.
- On this dataset, the strongest variance direction mostly reflects bathroom count, while the strongest component-to-price correlation is near zero. Neither result implies causation or useful predictive performance.
