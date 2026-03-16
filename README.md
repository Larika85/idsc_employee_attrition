# Employee Attrition Prediction Dashboard

A Streamlit web app to predict whether an employee is likely to stay or leave based on HR features and a trained ML pipeline (preprocessor + LDA + classifier).

## 🚀 Project Overview

This project includes a production-ready Streamlit interface (`app1.py`) that:
- Loads pre-trained artifacts (`pipeline.pkl` or `preprocessor.pkl`, `lda.pkl`, `best_model.pkl`)
- Accepts employee profile input (categorical and numeric) via UI controls
- Applies preprocessing, LDA transform, and model prediction
- Shows a styled card indicating likely stay/leave and prediction probability

## 📁 Repository Files

- `app1.py` — Streamlit app entrypoint
- `employee_cleaned.csv` — cleaned HR dataset used for defaults and schema
- `dataset1.csv` — supporting dataset
- `best_model.pkl` — trained classifier artifact
- `preprocessor.pkl` — preprocessing pipeline artifact
- `lda.pkl` — LDA transformation artifact
- `cols_info.pkl` — order of numeric/categorical columns
- `feature_info.pkl` — feature metadata
- `top_features.csv`, `top_features.pkl` — top selected features
- `requirements.txt` — Python dependencies
- `runtime.txt` — runtime configuration (for deployment platforms)
- `IDSC_PROJECT.ipynb` — Jupyter notebook for analysis and model building
- `IDSC_PPT.pdf` — project presentation

## ✅ Prerequisites

- Python 3.9+ (or compatible environment specified by `runtime.txt`)
- Installed dependencies in `requirements.txt`

## 🔧 Setup

1. **Clone this repo** (if not already):
   ```bash
   git clone <repo-url>
   cd idsc
   ```
2. **Create and activate a virtual environment**:
   ```bash
   python -m venv .venv
   .\.venv\Scripts\activate
   ```
3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## ▶️ Run the App

From the project root:
```bash
streamlit run app1.py
```
Open the URL shown by Streamlit (e.g. `http://localhost:8501`).

### 🌐 Live Deployment
You can also use the deployed app directly:
https://employee-attrition85.streamlit.app/

## 🧠 How It Works

1. `app.py` loads model artifacts with robust fallback logic:
   - Prefer `pipeline.pkl` when available
   - Otherwise load `preprocessor.pkl`, `lda.pkl`, and `best_model.pkl`
2. It loads column schema and defaults (from `cols_info.pkl` and `employee_cleaned.csv`).
3. The UI collects key HR features (department, role, overtime, satisfaction, etc.).
4. A single row is built in training order and processed.
5. The pipeline transforms inputs into LDA space and classifier outputs stay/leave with confidence.

## 📌 Notes for Reliability

- Prediction works best when the loaded artifacts come from the same training run.
- If preprocessing output features mismatch LDA input dimensions, the app shows an explicit error.
- The app automatically fills missing numeric/categorical values from dataset medians/modes.

## 🛠️ Customization

- To update model artifacts:
  1. Re-train your model with the same input schema.
  2. Save `preprocessor.pkl`, `lda.pkl`, `best_model.pkl` (or `pipeline.pkl`).
  3. Ensure `cols_info.pkl` contains `num_cols` and `cat_cols` in original training order.
- UI fields can be adjusted in `app.py` under the “Employee Information” section.

## 📈 Future Improvements

- Add real-time dataset validation + upload to allow custom data inference.
- Add batch inference and CSV export.
- Add user authentication and logging for production deployment.

## 🙋‍♂️ Contributions

Contributions are welcome! Please feel free to submit issues or pull requests.
