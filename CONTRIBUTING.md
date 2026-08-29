# Contributing to AgriViT-Plus

## Team Roles

| Role | Responsibility |
|---|---|
| CNN | CNN baseline, transfer learning, edge deployment |
| Generative | GAN + Diffusion models, data augmentation pipeline |
| Transformer | ViT implementation, attention visualization |
| Integration | Deployment pipeline, report coordination, analysis |

Cross-role collaboration is expected — role assignment sets primary accountability, not exclusive ownership. If you touch code outside your area, tag the relevant lead on the PR.

## Branching

- `main` — always working/deployable. No direct pushes.
- `feature/<short-description>` — one branch per feature or experiment (e.g. `feature/cnn-baseline`, `feature/attention-rollout`)
- `fix/<short-description>` — bug fixes

## Commits

Keep commit messages short and direct — one line describing what changed, imperative mood:

```
Add SE-ResNet block to CNN backbone
Fix ONNX export shape mismatch
Update training config for DeiT-Small
```

Avoid vague messages like `update`, `fix stuff`, `wip`. Squash noisy work-in-progress commits before opening a PR.

## Pull Requests

1. Branch off `main`, do your work, push your branch
2. Open a PR into `main` — describe *what* changed and *why* in 2–3 lines
3. At least one other team member reviews before merging
4. Delete the branch after merge

## Code Style

- Python: follow PEP8, use type hints where practical
- Keep model definitions in `models/`, training logic in `training/`, one-off exploration in `notebooks/` — don't mix experimental code into shared modules
- No large binary files (datasets, checkpoints) committed directly — use the links/instructions in `data/README.md` and the Weights section of `README.md` instead

## Reporting Issues

Use GitHub Issues for bugs, blockers, or experiment tracking. Tag with the relevant task label (`task-a`, `task-b`, `task-c`, `task-d`) so it's clear which section of the report it feeds into.

## Reproducibility

Any change to training scripts, hyperparameters, or data preprocessing should be reflected in the corresponding config file — not left as a manual code edit — so the whole pipeline stays reproducible end-to-end without contacting the author.
