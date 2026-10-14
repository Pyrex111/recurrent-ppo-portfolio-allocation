# Saved model

`ppo_best_model_seed25_round10.zip` is the unchanged Stable-Baselines3 checkpoint supplied with the project. It is a model archive, not a source-code ZIP; keep it zipped when using `RecurrentPPO.load`.

| Checkpoint metadata | Value |
| --- | --- |
| Algorithm | Recurrent PPO |
| Training seed | 25 |
| Selected round | 10, from the filename and saved notebook output |
| Recorded timesteps | 500,480 |
| Learning rate | 0.0001 |
| Rollout steps | 128 |
| Batch size | 64 |
| PPO epochs | 10 |
| Stable-Baselines3 | 2.6.0 |
| Python | 3.11.13 |
| PyTorch | 2.6.0+cu124 |
| Gymnasium | 1.1.1 |

The recorded timesteps can exceed the requested 50,000 per round because training collects complete rollouts. [training_system_info.txt](training_system_info.txt) is copied from the checkpoint's original system-information entry.

Use the 25-day, five-asset environment from the main notebook. The archived 2-day and 20-day versions have incompatible observation sizes. The original fitted scaler and downloaded data snapshot are not included.

The checkpoint contains model parameters, optimizer state, and serialized metadata. Publication inspected its ZIP contents and JSON metadata without loading those serialized objects. Inference was not run.

New notebook training outputs are saved in `models/runs/`, which is ignored by Git.
