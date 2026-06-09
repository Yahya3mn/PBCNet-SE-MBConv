# PBCNet-SE-MBConv

This repository provides the trained weights of the proposed **PBCNet-SE-MBConv** model developed for microscopic peripheral blood cell classification.

The model was trained for eight-class peripheral blood cell classification using the PBC dataset. The trained weights are shared to support reproducibility and future comparative studies.

---

## Model Overview

**PBCNet-SE-MBConv** is a custom convolutional neural network designed for peripheral blood cell classification. The architecture combines a convolutional stem, five MBConv-SE stages, depthwise convolution-based efficient feature extraction, squeeze-and-excitation based channel recalibration, optional residual connections with DropPath, and a compact classification head.

The model classifies peripheral blood cell images into the following eight classes:

| Index | Class |
|---:|---|
| 0 | Basophil |
| 1 | Eosinophil |
| 2 | Erythroblast |
| 3 | Immature granulocyte |
| 4 | Lymphocyte |
| 5 | Monocyte |
| 6 | Neutrophil |
| 7 | Platelet |

---

## Model Architecture

### Overall Architecture

![PBCNet-SE-MBConv architecture](docs/pbcnet_se_mbconv_architecture.jpg)

### MBConv-SE Block

![MBConv-SE block](docs/mbconv_se_block.jpg)

---

## Layer Configuration

| Stage | Operator | Expansion | Blocks | Stride | Output Size | Output Channels |
|---|---|---:|---:|---:|---|---:|
| Input | - | - | - | - | 224 × 224 | 3 |
| Stem-1 | Conv 3 × 3 | - | 1 | 2 | 112 × 112 | 32 |
| Stem-2 | Conv 3 × 3 | - | 1 | 1 | 112 × 112 | 32 |
| Stem-3 | Conv 3 × 3 | - | 1 | 2 | 56 × 56 | 64 |
| Stage 1 | MBConv-SE | 2 | 2 | 1 | 56 × 56 | 64 |
| Stage 2 | MBConv-SE | 4 | 3 | 2 | 28 × 28 | 96 |
| Stage 3 | MBConv-SE | 4 | 4 | 2 | 14 × 14 | 160 |
| Stage 4 | MBConv-SE | 4 | 4 | 2 | 7 × 7 | 256 |
| Stage 5 | MBConv-SE | 4 | 2 | 1 | 7 × 7 | 384 |
| Head | Conv 1 × 1, GAP, FC | - | 1 | - | 1 × 1 | 8 logits |

---

## Trained Model Weights

The trained weights of the proposed PBCNet-SE-MBConv model are available in the `weights/` directory.

```text
weights/pbcnet_se_mbconv_best.pth
```

## Citation

Y. Z. Khan, A. İnan, H. Kutucu, and İ. Avcı,
"Deep Learning-Based Peripheral Blood Cell Classification: Generalizability, Class Imbalance, and Explainability Analysis." (After publication citation will corrected)
