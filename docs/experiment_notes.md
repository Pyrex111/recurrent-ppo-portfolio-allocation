# Experiment notes

This repository publishes an existing individual ECE556 project. Preparation involved organizing supplied files, documenting them, replacing Google Drive paths, and extracting saved figures. Training, inference, market-data downloads, and metric calculation were not performed.

## Which notebook is the main experiment?

`notebooks/01_recurrent_ppo_lstm.ipynb` comes from `DRL_PPO_LSTM_Seeds.ipynb`. It contains seed 25, a 25-day observation window, ten recorded training rounds, best validation Sharpe 1.7522, and test Sharpe 1.4228. These match the final report and the supplied `ppo_best_model_seed25_round10.zip` checkpoint.

The original name suggests a multi-seed experiment, but the main notebook's `seeds` list contains only `[25]`. No multi-seed aggregate or statistical significance result is claimed.

`notebooks/02_markowitz_mvo.ipynb` is the supplied MVO baseline. Its saved outputs are validation Sharpe 2.6466 and test Sharpe 0.3283.

The two notebooks under `notebooks/archive/` are development versions. The early prototype uses a 2-day window and short training settings. The intermediate version uses a 20-day window, initializes models in a seed loop, and runs training outside that loop. Neither is the checkpoint-compatible main experiment, and neither was repaired or executed during publication.

## Report and implementation differences

| Item | Final report | Supplied implementation |
| --- | --- | --- |
| Test period | January–December 2024 | PPO standardized `test_returns` extends from January 2024 through June 2025; the raw-return argument passed to final evaluation ends in December 2024. The loop stops at the raw-return boundary. MVO test data is 2024 only. |
| Test coverage | Described as a test-set evaluation | PPO resets to a randomly selected start and uses an episode horizon of 180 steps, potentially shortened by the raw-return boundary. MVO starts at index 25 and runs 180 steps. These are not matching full-calendar backtests. |
| Baseline window | Section 6.4 describes 50 days | MVO `window_size = 25`. |
| Baseline costs | Section 6.4 describes zero transaction cost | MVO uses transaction-cost rate 0.0001 and allocation penalty weight 0.0005. |
| Baseline constraints | Section 6.4 describes normalization | MVO constrains weights to sum to one and bounds each weight between zero and one. |
| Round plots | Report captions label training-set plots | The main notebook constructs its per-round plots from validation evaluation arrays. The extracted round-10 figures are therefore labeled validation here. |

The PDFs are preserved as supplied, including these descriptions. Documentation identifies differences instead of changing the experiment retrospectively.

## Evaluation and reproducibility limitations

1. **Preprocessing includes held-out data.** Both notebooks fit `StandardScaler` over the full downloaded return history before splitting train, validation, and test periods. This introduces information from later periods into preprocessing.
2. **Financial calculations use different conventions.** PPO's reward environment computes returns from standardized inputs, while its reported evaluation uses unstandardized log returns converted to simple returns. MVO optimizes rolling moments of standardized inputs and evaluates adjusted log returns. Its Sharpe uses adjusted log returns; PPO's uses simple returns. Sharpe calculations assume a zero risk-free return.
3. **Costs are not applied equally in reported results.** PPO subtracts transaction and allocation-change penalties in the training reward, but its separate reported evaluation return does not subtract those costs. MVO subtracts costs and an allocation penalty from its evaluated returns.
4. **Allocation plots and evaluation use different weight representations.** The PPO environment normalizes actions for its step calculation and updates a smoothed internal weight state. The plot records that smoothed state. The separate validation/test calculation uses the raw output of `model.predict` without explicitly normalizing it. The plot therefore does not directly show the exact action used in the printed evaluation metric.
5. **Episode seeding is only partially controlled.** Validation explicitly calls `val_env.seed(seed)`. Test evaluation sets global random seeds but does not explicitly reseed its environment before reset; the environment has its own random state and default seed. Model seed 25 should not be interpreted as controlling every source of episode randomness.
6. **The original data/scaler snapshot is absent.** The notebooks request adjusted Yahoo Finance data up to June 30, 2025; the request end is exclusive. Data revisions and library behavior may alter later reruns. Prices, the fitted scaler, and an explicit ticker-to-`Asset_i` mapping were not included as separate files. The positional mapping follows downloaded column order.
7. **Evidence is limited to one saved experiment.** Five stocks, one main training seed, validation checkpoint selection, and individual evaluation episodes do not establish broad generalization or a statistically reliable advantage.

These limitations are retained for transparency. A future research revision could address them and generate new results, but this publication does not implement or claim that revision.

## Packaging changes

The setup no longer mounts Google Drive. Model and log paths are relative to the repository, and new checkpoints are written below `models/runs/` so the supplied checkpoint is kept separately. Notebook installation commands and setup messages are replaced by root-level dependency instructions. Introductory Markdown identifies the role of each notebook. See [file inventory](file_inventory.md) for the original names and checksums.
