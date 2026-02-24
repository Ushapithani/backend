
Resume Analysis API (Backend)
A FastAPI-based backend service that analyzes uploaded resume PDFs to extract skills, score the resume, and predict suitable career roles using a machine learning model.

Features

Accepts PDF resume uploads
Extracts text and detects key skills
Generates a resume quality score
Predicts top 3 career roles based on resume content
CORS enabled for integration with frontend (e.g., Next.js)


How It Works

User uploads a PDF resume
Server extracts text using pdfplumber
Skills are detected from predefined skill list
A machine learning model (Logistic Regression) predicts career roles
Returns structured JSON with resume score, extracted skills, and career recommendations


Tech Stack

FastAPI — backend API framework
uvicorn — ASGI server
scikit-learn — ML model
pdfplumber — PDF text extraction
pandas, numpy — data processing
Python-multipart — file upload support
joblib — model persistence


Repository Structure
backend
├── app.py
├── analyze_resume.py
├── requirements.txt
├── __pycache__/
├── model/
└── README.md

Installation
Step 1 — Clone the repo
bashgit clone https://github.com/Ushapithani/backend.git
cd backend
Step 2 — Create a virtual environment
bashpython3 -m venv venv
source venv/bin/activate   # macOS/Linux
venv\Scripts\activate      # Windows
Step 3 — Install dependencies
bashpip install -r requirements.txt

Running the API
bashuvicorn app:app --reload
```

By default the API is served at:
```
http://127.0.0.1:8000
```

---

## API Endpoints

### Test Server
```
GET /
Response:
json{
  "message": "Resume Analysis API is running!"
}
```

---

### Upload Resume
```
POST /predict
Input: PDF file
Returns: JSON with analysis
Example (cURL):
bashcurl -X POST "http://127.0.0.1:8000/predict" \
  -H "Content-Type: multipart/form-data" \
  -F "file=@resume.pdf"
Sample Response:
json{
  "success": true,
  "data": {
    "file_name": "resume.pdf",
    "score": 85,
    "skills": [],
    "insights": [],
    "career_primary": "Software Engineer",
    "career_alternatives": [],
    "predictions": []
  }
}
```

---

## Career Prediction Logic

The ML logic in `analyze_resume.py`:

- Uses a set of predefined career roles and skills
- Vectorizes skills from the resume
- Trains a Logistic Regression classifier on these role vectors
- Outputs top 3 predicted careers with confidence scores

---

## Notes

- Only PDF files are allowed
- CORS is configured for integration with frontend clients
- The model is trained on the fly using defined career roles

---

## Dependencies

From `requirements.txt`:
```
fastapi
uvicorn
scikit-learn
numpy
pandas
joblib
python-multipart
pdfplumber 

