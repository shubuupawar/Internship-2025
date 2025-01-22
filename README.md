# Machine Downtime Analysis
Internship Project work 

# Machine Downtime Analysis

## Overview
This project involves analyzing machine downtime data using a predictive model to classify whether a machine will fail or not based on sensor data. The process includes data cleaning, exploratory data analysis, model training, evaluation, and presenting results in JSON format.

## Steps to Run the Analysis

### 1. Prerequisites
Ensure you have the following installed:
- Python 3.8+
- Required Python libraries:
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - scikit-learn

You can install the necessary libraries using the following command:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### 2. Dataset
The dataset `Machine Downtime.csv` contains machine sensor readings and downtime statuses. The key features include:
- `Hydraulic_Pressure(bar)`, `Coolant_Pressure(bar)`, `Air_System_Pressure(bar)`
- `Coolant_Temperature`, `Hydraulic_Oil_Temperature(?C)`
- `Spindle_Bearing_Temperature(?C)`, `Spindle_Vibration(?m)`, `Tool_Vibration(?m)`
- `Spindle_Speed(RPM)`, `Voltage(volts)`, `Torque(Nm)`, `Cutting(kN)`
- `Downtime` (Target Variable)

### 3. Steps to Execute

#### A. Data Cleaning
1. Fill missing values in numerical columns with the median of the column.
2. Map the `Downtime` column to binary values (`Machine_Failure` -> `1`, `No_Failure` -> `0`).
3. Drop irrelevant columns: `Date`, `Machine_ID`, `Assembly_Line_No`.

#### B. Exploratory Data Analysis (EDA)
1. Visualize the correlation matrix to understand relationships between features.
2. Identify highly correlated features to improve model performance.

#### C. Model Training
1. Split the dataset into training and testing sets (80/20 split).
2. Train a Random Forest Classifier on the training data.

#### D. Model Evaluation
1. Generate a classification report including metrics like precision, recall, and F1-score.
2. Create a confusion matrix to analyze the performance of the classifier.
3. Output results in JSON format for structured analysis.

#### E. JSON Output
- Convert the classification report and confusion matrix to JSON format.
- Ensure compatibility with JSON by converting all NumPy data types to Python native types (e.g., `int64` -> `int`).

### 4. Running the Code
Run the Python script:
```bash
python machine_downtime_analysis.py
```

### 5. Example Output
#### JSON Classification Report:
```json
{
    "0": {
        "precision": 0.89,
        "recall": 0.92,
        "f1-score": 0.91,
        "support": 150
    },
    "1": {
        "precision": 0.85,
        "recall": 0.81,
        "f1-score": 0.83,
        "support": 100
    },
    "accuracy": 0.88,
    "macro avg": {
        "precision": 0.87,
        "recall": 0.87,
        "f1-score": 0.87,
        "support": 250
    },
    "weighted avg": {
        "precision": 0.88,
        "recall": 0.88,
        "f1-score": 0.88,
        "support": 250
    }
}
```

#### JSON Confusion Matrix:
```json
{
    "No_Failure": {
        "No_Failure": 138,
        "Machine_Failure": 12
    },
    "Machine_Failure": {
        "No_Failure": 19,
        "Machine_Failure": 81
    }
}
```

### 6. File Structure
```
├── Machine Downtime.csv
├── machine_downtime_analysis.py
├── README.md
```

## Notes
- Handle missing or unexpected values in the dataset carefully.
- The Random Forest Classifier can be replaced with other models if needed.
- JSON output ensures the results can be integrated into external systems easily.

Feel free to customize the code and dataset to fit specific use cases or additional features!


