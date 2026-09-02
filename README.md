# Deep Learning-Based Prediction of Coronary Heart Disease

A deep learning project for predicting 10-year Coronary Heart Disease (CHD) risk using the Framingham Heart Study dataset. The project compares a neural-network classifier trained on the original imbalanced dataset with the same model trained on a GAN-balanced dataset.

## Overview

Coronary Heart Disease prediction is challenging because CHD-positive cases are underrepresented in the Framingham dataset. This project investigates whether balancing the minority class with synthetic CHD-positive samples can improve deep-learning classification performance.

The research paper describes a GAN-based approach in which synthetic CHD-positive samples are generated and combined with real CHD-negative samples. The accompanying notebook evaluates two datasets:

- `framingham.csv` — original/imbalanced dataset
- `framingham MERGED.csv` — balanced dataset containing the augmented training data

> **Implementation note:** The uploaded notebook trains and evaluates the DNN on the two datasets; it does not contain the GAN-generation training code itself. Therefore, the GAN-balanced dataset should be treated as an input produced by a separate preprocessing/data-generation step.

## Dataset

The project uses the Framingham Heart Study dataset, containing demographic, lifestyle, medical-history, and clinical variables. The target is the binary `TenYearCHD` outcome representing whether CHD occurs within 10 years.

The research describes approximately 4,240 patient records and 15 input features. fileciteturn2file1L89-L99

For privacy and repository size reasons, do not upload sensitive/private patient data or large raw datasets unless you have permission to redistribute them.

## Methodology

The notebook follows these steps:

1. Load the Framingham dataset.
2. Remove rows containing missing values.
3. Separate features and the binary target.
4. Perform an 80:20 stratified train-test split.
5. Standardize the features using `StandardScaler`.
6. Build a feed-forward neural network.
7. Train the model using Adam and binary cross-entropy.
8. Evaluate using Accuracy, Precision, Recall, and F1-score.
9. Compare performance between the imbalanced and GAN-balanced datasets.

The research methodology also describes GAN-based minority-class generation and the use of a neural-network/MLP classifier. fileciteturn3file6L302-L331

## Model Architecture

The supplied Python implementation uses:

```text
Input Layer
    ↓
Dense Layer — 32 neurons, ReLU
    ↓
Dense Layer — 16 neurons, ReLU
    ↓
Output Layer — 1 neuron, Sigmoid
```

The model uses:

- Optimizer: Adam
- Loss: Binary Cross-Entropy
- Batch size: 32
- Random seed: 42
- Imbalanced dataset: 50 epochs
- Balanced dataset: 100 epochs
- Decision threshold: 0.5

## Results

According to the accompanying research paper, the comparison produced the following results:

| Metric | Imbalanced | GAN-Balanced |
|---|---:|---:|
| Accuracy | 82.56% | 84.28% |
| Precision | 81.66% | 83.17% |
| Recall | 81.61% | 85.89% |
| F1-score | 81.85% | 84.51% |

The largest improvement reported is in recall, increasing from 81.61% to 85.89%, while F1-score increases from 81.85% to 84.51%. fileciteturn3file3L153-L163

## Project Structure

```text
chd-deep-learning/
│
├── app.py
├── chd_gan.ipynb
├── README.md
├── requirements.txt
├── results/
│   └── graph.png
└── research/
    └── Deep_Learning_CHD_Research_Paper.docx
├── data/
│   └── framingham MERGED.csv
│   └── framingham.csv

Keep the datasets outside GitHub and explain in the README how to place them in the `data/` folder locally.

## Installation

Clone the repository and install the required packages:

```bash
pip install -r requirements.txt
```

## Running the Python Script

Place the required datasets in the project directory or update the dataset paths in `app.py`.

Then run:

```bash
python app.py
```

The Python script expects:

```text
framingham.csv
framingham MERGED.csv
```

The script trains one model on the imbalanced dataset and another on the balanced dataset.

## Running the Notebook

The notebook was prepared for Google Colab.

1. Open `chd_gan.ipynb` in Google Colab or Jupyter.
2. Upload `framingham.csv`.
3. Run the imbalanced-dataset section.
4. Upload `framingham MERGED.csv`.
5. Run the balanced-dataset section.
6. Compare Accuracy, Precision, Recall, and F1-score.

## Research Paper

**Deep Learning-Based Prediction of Coronary Heart Disease**

The paper investigates GAN-based class balancing for the Framingham Heart Study dataset and reports improved performance after synthetic minority-class augmentation. fileciteturn3file8L512-L532

## Limitations

The research notes that future work could investigate stronger tabular generative models such as CTGAN, TVAE, and diffusion models, as well as explainable-AI methods such as SHAP and LIME. fileciteturn3file3L170-L174

This project is intended for academic and research purposes and is **not a medical diagnostic system**.

## Author

**Serin Shabu**  
Undergraduate Student, Department of BCA  
Rajagiri College of Management and Applied Sciences, Kakkanad
