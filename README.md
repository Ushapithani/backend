
---

# 🚀 Resume Analysis API (Backend)

Welcome to the Resume Analysis API project! This FastAPI-based backend service analyzes uploaded resume PDFs to extract skills, score the resume, and predict suitable career roles using a machine learning model.

---

## ✨ Features

- 📄 **PDF Resume Upload:** Accepts and processes resume PDF files.
- 🧠 **Skill Extraction:** Detects key skills from resume content.
- 🎯 **Resume Scoring:** Generates a resume quality score.
- 💼 **Career Prediction:** Predicts top 3 career roles based on resume.
- 🌐 **CORS Enabled:** Ready for integration with frontend like Next.js.

---

## 📦 Requirements

- Python 3.8+
- FastAPI
- uvicorn
- scikit-learn
- pdfplumber
- pandas
- numpy
- joblib
- python-multipart

---

## 🧠 How It Works

1. User uploads a PDF resume
2. Server extracts text using `pdfplumber`
3. Skills are detected from predefined skill list
4. A Logistic Regression ML model predicts career roles
5. Returns structured JSON with score, skills, and career recommendations

---

## 🛠️ Tech Stack

- **FastAPI** — backend API framework
- **uvicorn** — ASGI server
- **scikit-learn** — ML model
- **pdfplumber** — PDF text extraction
- **pandas, numpy** — data processing
- **joblib** — model persistence

---

## 📁 Repository Structure

```
backend/
├── app.py
├── analyze_resume.py
├── requirements.txt
├── model/
└── README.md
```

---

## ⚙️ Installation

### Step 1 — Clone the repo
```bash
git clone https://github.com/Ushapithani/backend.git
cd backend
```

### Step 2 — Create virtual environment
```bash
python3 -m venv venv
source venv/bin/activate   # macOS/Linux
venv\Scripts\activate      # Windows
```

### Step 3 — Install dependencies
```bash
pip install -r requirements.txt
```

---

## 🚀 Running the API

```bash
uvicorn app:app --reload
```

Open browser at:
```
http://127.0.0.1:8000
```

---

## 📌 API Endpoints

### Test Server
```
GET /
```
Response:
```json
{
  "message": "Resume Analysis API is running!"
}
```

### Upload Resume
```
POST /predict
```
Example:
```bash
curl -X POST "http://127.0.0.1:8000/predict" \
  -H "Content-Type: multipart/form-data" \
  -F "file=@resume.pdf"
```

Sample Response:
```json
{
  "success": true,
  "data": {
    "file_name": "resume.pdf",
    "score": 85,
    "skills": [],
    "career_primary": "Software Engineer",
    "career_alternatives": []
  }
}
```

---

## 🎯 Career Prediction Logic

- Uses predefined career roles and skills
- Vectorizes skills extracted from resume
- Trains a Logistic Regression classifier
- Outputs top 3 predicted careers with confidence scores

---

## ❓ Notes

- Only PDF files are accepted
- CORS is configured for frontend integration
- Model is trained on the fly using defined career roles

---

## 👩‍💻 Developer

**Usha Pithani** — AI and Full Stack Developer

- Backend: https://github.com/Ushapithani/backend
- Frontend: https://github.com/Ushapithani/frontend

---

## 🏁 Project

This project is built as an AI-Based Career Recommendation System using ML. Suitable for Final Year Project, Hackathon, and Portfolio.

