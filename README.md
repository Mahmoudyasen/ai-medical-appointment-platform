# AI Medical Appointment Platform

A web platform where patients book and manage doctor appointments, and where machine learning models support diagnostic screening. Built with Next.js and MySQL, with Python (FastAPI) model services.

## Features

**For patients**
- Sign up and log in
- Browse the list of doctors and book appointments
- View, reschedule and cancel appointments
- **Symptom checker:** select symptoms; a Random Forest model predicts a likely condition and suggests which specialist to see

**For doctors**
- Separate doctor login
- Dashboard with profile information, incoming appointments and schedule
- Approve or cancel appointment requests

**ML services (`pages/*.py`)**
| Service | Model | Purpose |
|---|---|---|
| `model.py` | Random Forest with PCA and standard scaling (scikit-learn) | Disease prediction from symptoms |
| `hd.py` | Random Forest pipeline with imputation and one-hot encoding | Heart disease risk prediction |
| `brain_tumor_api.py` | TensorFlow SavedModel | Brain tumor classification from an uploaded MRI image |

## Tech stack

Next.js (pages router) · React · Tailwind CSS · shadcn/ui (Radix) · MySQL (`mysql2`) · FastAPI · scikit-learn · TensorFlow

## Running locally

1. Install dependencies:
   ```bash
   npm install
   ```
2. Create `.env.local` with your MySQL connection:
   ```
   DB_HOST=...
   DB_PORT=...
   DB_USER=...
   DB_PASSWORD=...
   DB_NAME=...
   ```
3. Start the symptom model service (the frontend calls `http://localhost:8000/model`):
   ```bash
   pip install fastapi uvicorn pandas numpy scikit-learn joblib
   cd pages && uvicorn model:app --port 8000
   ```
4. Start the web app:
   ```bash
   npm run dev
   ```
   Then open http://localhost:3000.

## Disclaimer

This is a student project. The models are for demonstration only and are not a medical device or a substitute for professional diagnosis.

## License

[MIT](LICENSE)
