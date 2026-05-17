<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a1628,40:0d2137,70:1a4a6e,100:0a1628&height=220&section=header&text=CoviSense&fontSize=72&fontColor=ffffff&fontAlignY=38&fontStyle=bold&desc=AI-Powered%20COVID-19%20Symptom%20Diagnosis%20%E2%80%94%20Served%20via%20Django&descSize=16&descAlignY=62&descColor=7eb8f7" width="100%"/>

<br/>

<p align="center">
  <img src="https://img.shields.io/badge/Django-Web%20Framework-092E20?style=for-the-badge&logo=django&logoColor=white"/>
  <img src="https://img.shields.io/badge/Machine%20Learning-COVID%20Diagnosis-1a4a6e?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-Model%20Training-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQLite-Database-003B57?style=for-the-badge&logo=sqlite&logoColor=white"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Forks-2-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/Stack-Django%20%2B%20ML%20%2B%20HTML%2FCSS%2FJS-092E20?style=flat-square"/>
  <img src="https://img.shields.io/badge/Domain-Healthcare%20AI-red?style=flat-square"/>
  <img src="https://img.shields.io/badge/Input-Symptom%20Based-orange?style=flat-square"/>
</p>

<br/>

> **CoviSense** is a full-stack COVID-19 symptom diagnosis web application — a machine learning model trained on symptom data is served through a Django backend with a complete HTML/CSS/JS frontend, allowing users to input symptoms and receive an AI-powered COVID-19 likelihood assessment.

<br/>

**[🧠 How It Works](#-how-it-works) · [🏗️ Architecture](#️-system-architecture) · [🚀 Quickstart](#-quickstart) · [📁 Project Structure](#-project-structure)**

</div>

---

## 🎯 Why This Exists

During the COVID-19 pandemic, early symptom screening was one of the most critical tools for reducing transmission. Clinics were overwhelmed, testing kits were scarce, and people had no reliable way to assess their risk at home before seeking medical attention.

CoviSense addresses this directly: enter your symptoms, get an AI-powered assessment of COVID-19 likelihood — instantly, privately, and without needing a clinic visit for an initial check.

---

## 🧠 How It Works

### Stage 1 — Model Training (Jupyter)

The core ML model is trained in `model.ipynb` using symptom-based patient data. The trained model is serialised and integrated into the Django backend for inference.

```
Symptom Data  →  Feature Engineering  →  ML Training  →  Serialised Model
```

### Stage 2 — Django Backend

Django serves as the application framework connecting the trained model to the web interface. The `COVID_19` app handles settings and configuration. The `manager` app handles business logic, views, URL routing, and model inference. The `Covid-19` module manages the diagnosis pipeline.

```python
# Django settings module
os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'COVID_19.settings')
```

### Stage 3 — Frontend Interface

A responsive HTML/CSS/JS frontend collects symptom inputs from the user and submits them to the Django backend. The prediction result is returned and rendered dynamically without page reload.

---

## ⚙️ System Architecture

```
User (Browser)
      │
      │  Symptom form submission
      ▼
Django Frontend (HTML + CSS + JS)
  Symptom input form
  Dynamic result rendering
      │
      │  POST request with symptom data
      ▼
Django Backend (COVID_19 settings + manager app)
  URL routing → View → Model inference
  SQLite for session and result storage
      │
      │  Symptom features
      ▼
ML Inference Engine
  Trained model loaded from serialised file
  Predicts COVID-19 likelihood from symptom vector
      │
      ▼
Diagnosis Result
  Returned to frontend and displayed to user
```

---

## ✨ Features

| Feature | Detail |
|---|---|
| 🔬 **Symptom-Based AI Diagnosis** | ML model predicts COVID-19 likelihood from user-reported symptoms |
| 🌐 **Full-Stack Django Application** | Complete web app with backend inference and frontend interface |
| 📊 **Model Training Notebook** | Reproducible Jupyter notebook for training and evaluating the model |
| 🗄️ **SQLite Database** | Lightweight database for storing sessions and results |
| 📱 **Responsive UI** | HTML/CSS/JS frontend works across desktop and mobile |
| 🔄 **ML to Web Pipeline** | End-to-end: raw data → trained model → Django API → browser |

---

## 📁 Project Structure

```
CoviDiagnoseServe/
│
├── COVID_19/                   Django project settings and configuration
│   ├── settings.py             Main settings (INSTALLED_APPS, DB, static files)
│   ├── urls.py                 Root URL configuration
│   └── wsgi.py                 WSGI application entry point
│
├── Covid-19/                   COVID diagnosis app module
│
├── manager/                    Core app — views, models, business logic
│   ├── views.py                Handles symptom input and prediction output
│   ├── models.py               Database models for storing results
│   └── urls.py                 App-level URL routing
│
├── frontend/                   HTML, CSS, JS interface
│   ├── templates/              Django template files
│   └── static/                 CSS, JS, and image assets
│
├── model.ipynb                 Jupyter notebook — ML model training and evaluation
├── manage.py                   Django management CLI
├── db.sqlite3                  SQLite database
└── README.md
```

---

## 🚀 Quickstart

### 1. Clone the repository

```bash
git clone https://github.com/mahmedmajeedai/CoviDiagnoseServe.git
cd CoviDiagnoseServe
```

### 2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install django scikit-learn pandas numpy joblib
```

### 4. Run the model training notebook (first time only)

Open `model.ipynb` in Jupyter and run all cells to train and serialise the model:

```bash
jupyter notebook model.ipynb
```

### 5. Apply database migrations

```bash
python manage.py migrate
```

### 6. Start the development server

```bash
python manage.py runserver
```

Open your browser at `http://127.0.0.1:8000` and start your symptom assessment.

---

## 🔬 The ML Model

The diagnosis model is trained on symptom-based COVID-19 patient data. The full training pipeline — data loading, preprocessing, feature engineering, model training, evaluation, and serialisation — is documented step by step in `model.ipynb`.

The serialised model is loaded by the Django backend on startup and used for inference on every symptom submission.

---

## ⚠️ Medical Disclaimer

CoviSense is an AI-assisted symptom screening tool built for educational and research purposes. It is not a substitute for professional medical advice, clinical diagnosis, or laboratory testing. Always consult a qualified healthcare provider for medical decisions.

---

## 🌍 Real-World Applications

| Use Case | Description |
|---|---|
| 🏠 **Home Pre-Screening** | Initial self-assessment before deciding to seek testing |
| 🏥 **Clinic Triage Support** | Assist healthcare workers in prioritising high-risk patients |
| 📊 **Epidemiological Research** | Anonymised symptom data collection for outbreak analysis |
| 🎓 **ML in Healthcare Education** | Reference implementation of end-to-end medical ML deployment |

---

## 📄 License

This project is open source. See [LICENSE](LICENSE) for details.

---

<div align="center">

**Built by [Muhammad Ahmed Majeed](https://github.com/mahmedmajeedai)**

*Full-stack machine learning for COVID-19 symptom screening*

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a4a6e,50:0d2137,100:0a1628&height=100&section=footer" width="100%"/>

</div>
