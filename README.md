# Malware Detection System Using Machine Learning and Deep Learning

## Project Overview
This project presents a comprehensive malware detection framework that leverages both traditional machine learning and deep learning techniques to accurately classify Portable Executable (PE) files as malicious or benign. It addresses the increasing sophistication of malware threats by combining feature-rich analysis with explainable AI methods.

The core innovation lies in extracting detailed structural and behavioral features from PE files—including headers, section information, entropy, and import/export tables—and feeding these into multiple predictive models such as XGBoost, Random Forest, K-Nearest Neighbors, and Long Short-Term Memory (LSTM) neural networks.

To enhance transparency, the system integrates SHAP (SHapley Additive exPlanations) values to interpret predictions and generate visual explanations, aiding cybersecurity analysts in understanding model decisions.

## Key Features
- **Robust Feature Extraction:** Utilizes the `pefile` Python library to parse PE files and extract hundreds of meaningful features, capturing metadata and binary characteristics relevant for malware classification.
- **Multiple Model Architectures:** Combines ensemble methods (XGBoost, Random Forest), traditional classifiers (KNN), and deep learning (LSTM, feedforward neural networks) to improve predictive accuracy and robustness.
- **Explainability with SHAP:** Offers model-agnostic interpretability by calculating SHAP values, providing insights on which features contribute most to classifying a file as malware or benign.
- **Flask-Based REST API:** Enables easy integration by exposing an API endpoint that accepts PE files, performs real-time prediction, and returns results including probabilities, textual explanations, and graphical SHAP plots.
- **Visualization Tools:** Provides interactive and static plots such as ROC curves, learning curves, and bar charts for performance comparison among models.
- **Data Preprocessing Pipeline:** Includes imputation, scaling, tokenization, and sequence padding to handle diverse data types and prepare inputs suitable for each model.
- **Model Evaluation:** Implements detailed metrics such as accuracy, precision, recall, F1-score, confusion matrix, and ROC-AUC to rigorously assess model performance.

## Getting Started

### Prerequisites
- Python 3.7 or later
- Basic familiarity with command-line interfaces
- Dataset containing labeled PE files and their extracted features (`dataset_malwares.csv`)

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/malware-detection.git
    cd malware-detection
    ```

2. (Optional) Create and activate a virtual environment to isolate dependencies:
    ```bash
    python3 -m venv venv
    source venv/bin/activate    # On Windows use: venv\Scripts\activate
    ```

3. Install the required Python packages:
    ```bash
    pip install -r requirements.txt
    ```

4. Place your dataset file (`dataset_malwares.csv`) in the project directory or update the paths accordingly.

### Dataset Format
The dataset should contain:
- **Features:** Numeric and categorical attributes extracted from PE files (e.g., headers, entropy, section sizes).
- **Target column:** Binary label indicating malware presence (`Malware` column).
- **File names:** Optional `Name` column, which is ignored during training.

### Usage

#### Training Models
Use the provided training scripts (e.g., `model_training.py`) to preprocess data, train multiple models, and save the best-performing models to disk. This step includes feature scaling, imputation of missing values, and tokenization for sequential features.

#### Running the Flask API
Launch the Flask API to serve predictions and explanations via REST endpoints:
```bash
python app.py
