# Original saved results

Values and figures here are taken from the supplied notebook outputs. No training, evaluation, or chart regeneration was performed during publication.

| Saved metric | Value | Source |
| --- | ---: | --- |
| PPO best validation Sharpe | 1.7522 | Main notebook, seed 25, round 10 |
| PPO test Sharpe | 1.4228 | Main notebook, final evaluation output |
| MVO validation Sharpe | 2.6466 | Baseline notebook, validation output |
| MVO test Sharpe | 0.3283 | Baseline notebook, test output |

## PPO validation history

| Round | Saved validation Sharpe |
| --- | ---: |
| 1 | 0.8645 |
| 2 | 0.8162 |
| 3 | 0.7462 |
| 4 | 1.2315 |
| 5 | 1.1302 |
| 6 | 1.2267 |
| 7 | 1.4035 |
| 8 | 1.6340 |
| 9 | 1.3126 |
| 10 | 1.7522 |

## Figure provenance and conventions

| Saved figure | Meaning |
| --- | --- |
| [PPO round-10 return plot](figures/ppo_round10_validation_returns.png) | Validation episode after round 10; sum of simple returns |
| [PPO round-10 weights](figures/ppo_round10_validation_weights.png) | Smoothed environment weight state during that validation episode |
| [PPO test return plot](figures/ppo_test_returns.png) | Final test evaluation; sum of simple returns |
| [PPO test weights](figures/ppo_test_weights.png) | Smoothed environment weight state in the final test evaluation |
| [MVO test return plot](figures/mvo_test_returns.png) | Compounded return from the baseline's adjusted log returns |
| [MVO test weights](figures/mvo_test_weights.png) | Baseline optimizer allocations during its test episode |

The PPO charts use `np.cumsum(simple_returns)`, while the MVO chart compounds `np.exp(adjusted_log_returns)`. Their plotted cumulative returns are not calculated on the same basis. The PPO weight charts show a smoothed internal state, rather than the raw policy action used by its separate evaluation function.

Read [experiment notes](../docs/experiment_notes.md) before interpreting the PPO/MVO comparison. Notebook figures use positional labels such as `Asset 1`; the original download's column-to-ticker mapping was not saved separately.
