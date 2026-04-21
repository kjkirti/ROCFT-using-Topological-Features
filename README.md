# Automatic Scoring of the Rey-Osterrieth Complex Figure Test Using Topological Features

A machine learning pipeline that automatically scores Rey-Osterrieth Complex Figure Test (ROCFT) drawings using Topological Data Analysis (TDA) via the Giotto-TDA library.

---

## Overview

The Rey-Osterrieth Complex Figure Test (ROCFT) is a neuropsychological evaluation tool used to assess visuo-constructional ability, visual memory, attention, fine-motor coordination, and spatial orientation. Traditionally scored by hand, this project explores whether topological features extracted from ROCFT drawings can be used to automate the scoring process.

---

## Dataset

- **416 images** total: 208 copied drawings + 208 recalled drawings
- Each image is paired with a hand-evaluated score (stored in CSV format)
- Images were pre-processed into grayscale and downscaled to **40% of original size** (original: 354×500 px) for computational efficiency
- Scores range from **0 to 36**

---

## Methodology

### Libraries Used
- `Giotto-TDA (gtda)` — Topological Data Analysis
- `PIL` / `OpenCV` — Image loading and preprocessing
- `TensorFlow / Keras` — Neural network model
- `scikit-learn` — ML utilities

### Pipeline Steps

1. **Data Loading** — Images loaded using the `glob` module
2. **Preprocessing** — Resize to 40%, flatten pixel arrays
3. **Binarization** — Using Giotto-TDA's `Binarizer` class
4. **Persistent Homology** — Persistence diagrams constructed via `CubicalPersistence`
5. **Feature Extraction** — Amplitude and persistence entropy computed across multiple metrics and height filtration directions
6. **Feature Union** — All topological features combined into a single feature vector per image
7. **Model Training** — Feedforward neural network trained on extracted features

---

## Author

**Kirti Jha**  
M.Sc. Data Science, Universität Erlangen-Nürnberg (FAU)  
kirti.jha@fau.de
