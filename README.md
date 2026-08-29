# AgriViT-Plus

CNN-ViT hybrid with cross-attention fusion for precision agriculture — edge-ready crop health detection.

> **Status: 🚧 Training in progress.** Baseline CNNs and the hybrid CNN-ViT architecture are currently being trained/evaluated. Benchmark numbers, exported ONNX weights, and edge-deployment results will be added as they become available.

## Overview

AgriViT-Plus combines the local, texture-sensitive feature extraction of CNNs with the global context modeling of Vision Transformers, fused via cross-attention, to classify crop health from field/leaf imagery. The design targets both **accuracy** (competitive with pure CNN/ViT baselines) and **deployability** (lightweight enough for edge inference on devices like Raspberry Pi / Jetson Nano).

Core components:
- **CNN backbone** — SE-ResNet blocks for local feature extraction
- **ViT branch** — patch-based transformer encoder for global context
- **Cross-attention fusion** — combines CNN and ViT feature streams
- **Training** — focal loss with label smoothing to handle class imbalance in agricultural datasets
- **Deployment pipeline** — ONNX export, targeting edge devices

## Datasets

Training and evaluation currently use the following benchmark agricultural datasets:

| Dataset | Domain | Size | Task |
|---|---|---|---|
| [PlantVillage](https://www.kaggle.com/datasets/emmarex/plantdisease) | Plant disease | 54,306 images | Classification, segmentation |
| [PlantDoc](https://github.com/pratikkayal/PlantDoc-Dataset) | Plant disease (wild/field conditions) | 2,569 images | Classification (harder, real-world variability) |
| [DeepWeeds](https://github.com/AlexOlsen/DeepWeeds) | Weed detection | 15,007 images | Classification |

*(Add/remove rows here as additional datasets — e.g. WeedMap, AgriNet, Maize Seed — are brought into the pipeline.)*

Dataset download instructions and preprocessing scripts are in [`data/`](./data) — see `data/README.md` for per-dataset setup steps.

## Repository Structure

```
agrivit-plus/
├── data/               # dataset download + preprocessing scripts
├── models/             # model definitions (CNN baseline, ViT, hybrid CNN-ViT)
├── training/           # training loops, configs, loss functions
├── notebooks/          # exploratory / experiment notebooks
├── weights/            # saved checkpoints (not committed — see Weights below)
├── export/             # ONNX export + quantization scripts
├── mylogs/             # experiment tracking (not committed — see Experiment Tracking below)
│   ├── tensorboard/
│   ├── mlflow/
│   └── optuna/
├── requirements.txt
├── README.md
├── LICENSE
└── CONTRIBUTING.md
```

## Environment Setup

```bash
# clone
git clone https://github.com/<your-username>/agrivit-plus.git
cd agrivit-plus

# create environment
conda create -n agrivit python=3.10 -y
conda activate agrivit
pip install -r requirements.txt
```

Key dependencies: PyTorch ≥2.0, torchvision, timm, torchmetrics.

## Training

```bash
# example: train the CNN baseline
python training/train.py --model cnn_baseline --dataset plantvillage --epochs 50

# train the hybrid CNN-ViT
python training/train.py --model agrivit_plus --dataset plantvillage --epochs 100
```

*(Update flags/paths above to match your actual training script once finalized.)*

## Evaluation

```bash
python training/evaluate.py --model agrivit_plus --checkpoint weights/agrivit_plus_best.pt --dataset plantvillage
```

Reports accuracy, F1-score, confusion matrix, and Grad-CAM/attention visualizations.

## Experiment Tracking

Training runs are logged to `mylogs/` (git-ignored — regenerate locally by re-running training):

```python
# TensorBoard
writer = SummaryWriter(log_dir="mylogs/tensorboard")

# MLflow
mlflow.set_tracking_uri("mylogs/mlflow")

# Optuna
study = optuna.create_study(
    storage="sqlite:///mylogs/optuna/study.db",
    study_name="agrivit_plus"
)
```

View logs locally:

```bash
tensorboard --logdir mylogs/tensorboard
mlflow ui --backend-store-uri mylogs/mlflow
```

## Model Weights

Trained weights are not committed to the repo due to size. Once training completes, weights will be uploaded and linked here (Google Drive / Kaggle / GitHub Releases).

## Roadmap

- [x] Data pipeline + preprocessing
- [ ] CNN baseline training
- [ ] Hybrid CNN-ViT (AgriViT-Plus) training
- [ ] Ablation studies (frozen layers, LR schedule, augmentation intensity)
- [ ] ONNX export + INT8 quantization
- [ ] Edge deployment benchmarks (Raspberry Pi / Jetson Nano)

## Acknowledgments

Architecture and experimental design inspired by recent work on hybrid CNN-Transformer models for precision agriculture, including Hassan et al., *"Next-Generation Smart Agriculture: A Review of Deep Learning–Based Computer Vision Approaches,"* Array (2026).

## License

MIT — see [LICENSE](./LICENSE)
