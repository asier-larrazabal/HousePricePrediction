# HousePricePrediction — Reproducibility & Chronos instructions

This repository contains `00_Analysis.ipynb` for the California ZHVI forecasting project.

## Reproducibility (local)
1. Create and activate a virtual environment (Windows PowerShell):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Upgrade pip and install requirements:

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

3. Launch Jupyter Notebook and run `00_Analysis.ipynb`.

```powershell
jupyter notebook
```

Notes:
- `chronos-forecasting` may require `torch` with a compatible CUDA build to use GPU. If you face conflicts with a package named `chronos`, uninstall it first: `pip uninstall chronos`.
- If you cannot run Chronos locally (dependency or GPU constraints), run the Chronos cell in Google Colab — the notebook documents that the original Chronos run was executed in Colab.

## Chronos (local) — guidance
- Prefer a Linux or Conda environment for easier CUDA + PyTorch management.
- Install a compatible PyTorch build first (see https://pytorch.org/get-started/locally/).

Example (CPU-only):

```powershell
pip install torch --index-url https://download.pytorch.org/whl/cpu
pip install chronos-forecasting
```

If you have GPU (Windows):
- Follow PyTorch website instructions to install the correct CUDA wheel.
- Then `pip install chronos-forecasting`.

## Chronos (Google Colab)
1. Open a new Colab notebook and upload `00_Analysis.ipynb`.
2. In Colab, run:

```python
!pip install chronos-forecasting
```

3. Execute the Chronos cell. Download checkpoints/outputs if needed.

## Notes about exogenous forecasting
- The notebook now includes a small pipeline to auto-ARIMA-forecast the exogenous series (`InventorySeasonallyAdjusted_AllHomes`) and re-run SARIMAX with the forecasted exog (no oracle).

## Outputs
- Add an `outputs/` folder to store saved models (`joblib`/`pickle`) and exported plots (PNG) if required.

If you want, I can also:
- pin exact package versions using `pip freeze > requirements.txt` from the environment you used; or
- create an `environment.yml` for Conda.
