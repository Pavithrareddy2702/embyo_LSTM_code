# Embryo Stage Classification using LSTM

# Models Used

This project uses:
- MobileNetV2 (CNN for feature extraction)
- LSTM (for sequence learning)

# Dataset

- Embryo image dataset from Kaggle
- Total images loaded: 19,747
- Total classes: 16 embryo stages
- Images resized to 128 × 128

Dataset split was done embryo-wise:

| Set | Number of Embryos folders used |
|---|---|
| Training | 37 |
| Testing | 10 |


# How the Model Works

Instead of using one image, the model uses sequences of 5 frames.

Example:

```python
[frame1, frame2, frame3, frame4, frame5] → final stage prediction
```

The CNN extracts features from each frame, and the LSTM learns the sequence pattern.

---

# Model Architecture

```python
Input → MobileNetV2 → GlobalAveragePooling → LSTM → Dense → Softmax
```

- MobileNetV2 was used as feature extractor
- LSTM learns temporal information from frame sequences
- Final dense layer predicts one of 16 stages

---

# Training Details

- Optimizer: Adam
- Learning Rate: 0.0001
- Batch Size: 16
- Epochs: 30


# Final Results

| Metric | Value |
|---|---|
| Train Accuracy | 79.03% |
| Validation Accuracy | 43.75% |
| Test Accuracy | 46.97% |
| Test Loss | 1.5873 |


# Observations

- The model learned training data well.
- Test accuracy was lower compared to training accuracy.
- The model showed overfitting.
- Small dataset size may be one reason for lower performance.
