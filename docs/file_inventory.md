# File inventory and publication changes

All seven supplied project files are included. These are the filename mappings:

| Supplied filename | Repository file |
| --- | --- |
| `DRL_PPO_LSTM_Seeds.ipynb` | [`notebooks/01_recurrent_ppo_lstm.ipynb`](../notebooks/01_recurrent_ppo_lstm.ipynb) |
| `MVO_Markowitz.ipynb` | [`notebooks/02_markowitz_mvo.ipynb`](../notebooks/02_markowitz_mvo.ipynb) |
| `DRL_PPO+LSTM.ipynb` | [`notebooks/archive/ppo_lstm_early_prototype.ipynb`](../notebooks/archive/ppo_lstm_early_prototype.ipynb) |
| `DRL_PPO+LSTM_without_seeds.ipynb` | [`notebooks/archive/ppo_lstm_intermediate.ipynb`](../notebooks/archive/ppo_lstm_intermediate.ipynb) |
| `DRL Project Report-Public.pdf` | [`docs/project_report.pdf`](../docs/project_report.pdf) |
| `DRL Presentation-V3 - Final.pdf` | [`docs/presentation.pdf`](../docs/presentation.pdf) |
| `ppo_best_model_seed25_round10.zip` | [`models/ppo_best_model_seed25_round10.zip`](../models/ppo_best_model_seed25_round10.zip) |

The two PDFs and the checkpoint ZIP are byte-for-byte copies of the supplied files.
The four notebooks retain their experiment code and saved result figures, with these publication edits:

- Added introductory Markdown identifying main, baseline, and archived notebooks.
- Removed notebook installation commands and their setup output; dependencies are listed at the repository root.
- Removed Google Colab Drive mounting and replaced model/log paths with repository paths.
- New training output paths use `models/runs/`; the evaluation path uses the supplied checkpoint under `models/`.
- Added notebook cell IDs and removed Colab-specific GPU metadata.
- Updated the printed historical model-save path to its local equivalent. Numeric results are unchanged.

No models were trained, notebooks executed, market data downloaded, or metrics recomputed during publication.
The PNG files in `results/figures/` were decoded directly from saved notebook outputs.
The checkpoint was inspected as a ZIP and JSON metadata only; its serialized Python/PyTorch objects were not loaded.

## Checksums of supplied files

These SHA-256 checksums identify the original uploaded bytes, before notebook packaging edits.

| Original filename | SHA-256 |
| --- | --- |
| `DRL_PPO_LSTM_Seeds.ipynb` | `b70aed8ff761488eb1a117e4205a1dcd3ff3adbb26186aa8f7521ad121f76340` |
| `MVO_Markowitz.ipynb` | `178b5c7a2c875152bed039f8cc21c762c02d54ec7a02938816f963d04b2cdede` |
| `DRL_PPO+LSTM.ipynb` | `fdceb3138c6648ff67388039dce9932cec2aaecd674bdab7ba8964f3554a6149` |
| `DRL_PPO+LSTM_without_seeds.ipynb` | `32e9b7ccc3edc349746f575933f6d4ee76ca4eccbfa8a9dc3b8c9c9c5cc117a1` |
| `DRL Project Report-Public.pdf` | `a6f808958514c49d98bae435716fcc4eb44d17e6b84ec3dcc3fb085761a46a84` |
| `DRL Presentation-V3 - Final.pdf` | `772d0a37203a5a5d5f83bf801ff34a150a4e459040f662997145e2f1e97cc95d` |
| `ppo_best_model_seed25_round10.zip` | `818964055394dbd729ee7c22a28ec4a86ee438e90d611951f3a6a2dd632714ee` |
