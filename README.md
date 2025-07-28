
# 🛵 Swiggy Delivery Time Prediction

This project predicts the **delivery time** of food orders on Swiggy using machine learning. It uses structured data such as location, delivery partner information, and order details. The project also integrates **MLflow** for experiment tracking, **DVC** for data versioning, and is deployed on **AWS EC2 with Auto Scaling Group (ASG)** and **AWS CodeDeploy** for scalable, automated deployment.

---

## 🚀 Project Overview

We aim to accurately predict the `Time_taken(min)` for a food delivery order. This helps improve:
- Delivery time estimations
- Customer satisfaction
- Logistics efficiency

---

## 🧠 Features Used

- **Delivery Person**: Age, Ratings  
- **Location Data**: Restaurant & Delivery latitude/longitude  
- **Order Type**: Food category, vehicle type  
- **Distance**: Haversine formula used to compute geo-distance

---

## 📊 Dataset

- 📁 Location: `data/raw/delivery_data.csv`  
- 📌 Source: Cleaned Kaggle dataset (courtesy of Gaurav Malik)  
- 🔢 Target Column: `Time_taken(min)`  
- 🧹 Preprocessing includes:
  - Handling missing values
  - Distance feature calculation
  - One-hot encoding

---

## 🧰 Tech Stack

| Area               | Tool/Library                        |
|--------------------|-------------------------------------|
| ML & Preprocessing | `pandas`, `scikit-learn`, `joblib`, `lightgbm`  |
| Model Ensemble     | `StackingRegressor` with `RandomForestRegressor` & `LGBMRegressor` |
| Experiment Tracking| `MLflow`                            |
| Data Versioning    | `DVC`                               |
| Deployment         | `AWS EC2`, `Auto Scaling Group`, `CodeDeploy` |
| CI/CD              | `GitHub Actions`                    |

---

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/Himanshu-1703/swiggy-delivery-time-prediction.git
cd swiggy-delivery-time-prediction
```

### 2. Set up Python environment

```bash
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Initialize DVC and MLflow

```bash
dvc pull   # Pulls versioned data
mlflow ui  # Optional: view experiment dashboard
```

---

## 🧠 Model Info

The best models identified through MLflow experimentation include:
- ✅ **Random Forest Regressor**
- ✅ **LightGBM Regressor**
- ✅ **Stacking Regressor** combining both above for improved performance

Models are tracked in MLflow and versioned with DVC for reproducibility.

---

## 📈 MLflow Usage

To run and log an experiment:
```bash
python src/models/train_model.py
```
View the MLflow dashboard:
```bash
mlflow ui
```

---

## 📦 DVC Usage

```bash
dvc repro        # Reproduce entire pipeline
dvc push         # Push data/models to remote storage
```

---

## ☁️ Deployment (AWS CodeDeploy + ASG)

- Dockerized app zipped with `appspec.yml`
- Uploaded to S3 and deployed using CodeDeploy to EC2 (in ASG)
- Trigger deployment via GitHub Actions or AWS CLI

---

## 💻 Run Locally

```bash
streamlit run app.py
```

---

## 🔁 Makefile Commands

```bash
make data     # Process data
make train    # Train and log with MLflow
make predict  # Run predictions
```

---

## 🤝 Contributing

1. Fork this repo
2. Create your feature branch: `git checkout -b feature/my-feature`
3. Commit changes: `git commit -am 'Add feature'`
4. Push and open a Pull Request

---

## 📄 License

MIT License. See [LICENSE](./LICENSE) for details.

---

## 🙏 Acknowledgements

- Gaurav Malik (Kaggle dataset)
- [MLflow](https://mlflow.org)
- [DVC](https://dvc.org)
- [AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/)
- [Streamlit](https://streamlit.io)

---

> **⭐ If you found this helpful, please star the repo!**
