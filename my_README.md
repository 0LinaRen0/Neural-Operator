# DW0136 — Seismic inversion & denoising (中英双语)

本仓库包含用于地震反演与去噪的实验代码，包含三个主要工作流：

- `code/in_distribution/`：分布内实验（DDPM + Neural Operator）
- `code/overthrust/`：Overthrust 数据集的反演实现
- `code/volve_data/`：Volve 数据的清洗与反演工作流

---

# DW0136 — Seismic inversion & denoising (EN)

This repository contains code for seismic inversion and denoising experiments. Main workflows:

- `code/in_distribution/`: in-distribution experiments (DDPM + Neural Operator)
- `code/overthrust/`: Overthrust inversion pipeline
- `code/volve_data/`: Volve data cleaning and inversion

Repository layout / 仓库结构

- `asset/` — project assets (icons, images)
- `code/`
  - `in_distribution/` — DDPM + Neural Operator modules
  - `overthrust/` — Overthrust inversion modules
  - `volve_data/` — Volve workflow and utilities
- `data/` — dataset folders and pretrained models
- `opl.yml` — conda environment specification
- `install_env.sh` — helper to create and activate environment
- `pyproject.toml` — project metadata

Key modules (主要模块)

code/in_distribution/

- `config.py`: paths and hyperparameters
- `style.py`: plotting fonts and styles
- `data.py`: datasets, loaders, normalization
- `models.py`: HybridFNO and FNO-UNet-FNO
- `train.py`: training and validation routines
- `diffusion.py`: DDPM loading and utilities
- `inversion.py`: velocity inversion loop (supports DDPM)
- `plotting.py`: plotting helpers
- `my_code_ddpm_simple_true_clean.ipynb`: main notebook

code/overthrust/

- `config.py`: path and inversion config
- `dataset.py`: `.npy` loading and dataset
- `models.py`: neural operator and helpers
- `losses.py`: ERTM and gradient-weighted losses
- `inversion.py`: inversion loop (use_ddpm True/False)
- `plotting.py`: visualization utilities
- `run_overthrust_inversion.py`: main runner

code/volve_data/

- `Volve_test_clean.ipynb`: main notebook
- `volve_utils/`: modular utilities (config, data, models, ddpm_wrapper, inversion, plotting)

Installation / 安装

1. Create the conda environment with `opl.yml` (recommended):

```bash
./install_env.sh
```

If Conda is in a non-standard location, load it first:

```bash
source ~/anaconda3/etc/profile.d/conda.sh
# or
source ~/miniconda3/etc/profile.d/conda.sh
conda activate MSMHA
```

Run / 运行方式

- `code/in_distribution`: open `my_code_ddpm_simple_true_clean.ipynb`, run cells in order. Change `config.py` / `InversionConfig()` for paths and parameters.

- `code/overthrust`: run the main script:

```bash
cd code/overthrust
python run_overthrust_inversion.py
```

Adjust `INV_CFG` in `config.py` as needed.

- `code/volve_data`: open `Volve_test_clean.ipynb`, update the top configuration cell, then run.

Data folders / 数据说明

- `data/in_distribution/`: training images, velocity fields, DDPM checkpoints
- `data/overthrust/`: Overthrust inputs, models, and results
- `data/volve/`: Volve inputs, models, and results

Compatibility / 兼容性

- Python >= 3.8 (see `pyproject.toml`)
- This repo expects CUDA-capable PyTorch (example: CUDA 11.8). Run on GPU if available.

Notes / 备注

- For quick experiments, open the notebook or runner in the relevant `code/` subfolder.
- `config.py` files are the primary user-editable entry points for paths and parameters.

---

If you want, I can:

- add a short QuickStart example per workflow (ZH/EN), or
- include common troubleshooting tips (Cond a/PyTorch/CUDA), or
- generate a brief changelog template for experiments.

