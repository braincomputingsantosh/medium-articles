# EEG-based Stress Detection System

A machine learning system for detecting stress levels using EEG (Electroencephalography) signals. This implementation demonstrates how to classify mental states (relaxed, neutral, stressed) using various machine learning algorithms.

## 📊 Overview

This project implements an EEG-based stress detection system based on the research paper "Contribution of EEG Signals for Students' Stress Detection". The system uses synthetic EEG data to demonstrate:

- Feature extraction from multi-channel EEG signals
- Classification using multiple ML algorithms (LightGBM, KNN, SVM)
- Real-time stress detection simulation
- Comprehensive performance visualization

## 🚀 Features

- **Multi-channel EEG Processing**: Supports 19-channel EEG based on the 10-20 system
- **Feature Extraction**: Extracts mean and standard deviation features from EEG windows
- **Multiple Classifiers**: Compares LightGBM, K-Nearest Neighbors, and Support Vector Machine
- **Class Balancing**: Implements random oversampling for balanced training
- **Real-time Demo**: Simulates real-time stress detection
- **Comprehensive Visualization**: Includes performance metrics, confusion matrices, and feature importance

## 📋 Requirements

- Python 3.8+
- NumPy
- Pandas
- Scikit-learn
- LightGBM
- Matplotlib
- Seaborn
- SciPy

## 🛠️ Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd eeg-stress-detection
```

2. Create a virtual environment (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## 💻 Usage

### Basic Usage

Run the main script to see the complete demonstration:

```bash
python eeg_stress_detection.py
```

This will:
1. Generate synthetic EEG data for 30 subjects
2. Extract features from the EEG signals
3. Train and compare three different classifiers
4. Display performance visualizations
5. Run a real-time stress detection demo

### Using as a Module

```python
from eeg_stress_detection import EEGStressDetector

# Initialize detector
detector = EEGStressDetector(n_channels=19, sampling_rate=500, window_size=1)

# Generate synthetic data
data_dict = detector.generate_synthetic_eeg_data(n_subjects=30, duration_minutes=22)

# Extract features
features, labels = detector.extract_features(data_dict['data'], data_dict['labels'])

# Balance classes
X_balanced, y_balanced = detector.balance_classes(features, labels)

# Train models
results = detector.train_models(X_balanced, y_balanced)

# Visualize results
detector.plot_results(results)
```

## 📊 Output

The system generates several visualizations:

1. **Model Performance Comparison**: Bar chart comparing accuracy, precision, and F1-score
2. **Confusion Matrix**: Shows classification performance for the best model
3. **Feature Importance**: Displays the most important EEG channels (for LightGBM)
4. **Cross-validation Scores**: Shows model stability across different data splits
5. **Real-time Demo**: Simulates stress detection over time

## 🧠 EEG Channels

The system uses the standard 10-20 EEG electrode placement system with 19 channels:
- Frontal: Fp1, Fp2, F7, F3, Fz, F4, F8
- Temporal: T7, T8
- Central: C3, Cz, C4
- Parietal: P7, P3, Pz, P4, P8
- Occipital: O1, O2

## 📈 Performance

Typical performance metrics (on synthetic data):
- Accuracy: ~85-95%
- Precision: ~85-95%
- F1-Score: ~85-95%

*Note: Performance on real EEG data may vary significantly*

## ⚠️ Limitations

- This implementation uses **synthetic data** for demonstration purposes
- Real EEG data requires additional preprocessing (artifact removal, filtering, etc.)
- The simple feature set (mean & std) is for demonstration; real applications may need more sophisticated features
- Clinical applications require proper validation and regulatory approval

## 🔬 Extending the System

To adapt this system for real EEG data:

1. Replace the `generate_synthetic_eeg_data()` method with real data loading
2. Add preprocessing steps (artifact removal, band-pass filtering, etc.)
3. Implement additional features (power spectral density, coherence, etc.)
4. Consider deep learning approaches for automatic feature learning
5. Add proper cross-subject validation

## 📚 References

- Based on: "Contribution of EEG Signals for Students' Stress Detection"
- EEG 10-20 System: International standard for electrode placement
- Feature extraction methods inspired by common EEG analysis practices

## 📄 License

This project is licensed under the MIT License.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📧 Contact

For questions or suggestions, please open an issue on GitHub.

---

**Disclaimer**: This is a demonstration system using synthetic data. It is not intended for medical diagnosis or clinical use.