# SIPETANI — AI Plant Disease Detector

<img width="400" height="280" alt="Screenshot 2026-07-07 150429" src="https://github.com/user-attachments/assets/2e12ddc9-5248-4ca7-9f7d-6c0f255f9e72" />
<img width="400" height="280" alt="Screenshot 2026-07-07 150638" src="https://github.com/user-attachments/assets/cc99a734-3166-402e-9a57-3568a73e498c" />


## Overview
SIPETANI is an end-to-end, AI-powered agricultural platform designed to help farmers identify crop diseases and pests in real-time through leaf images. The system integrates a custom-trained YOLOv8 deep learning model capable of precisely detecting, classifying, and localizing multiple plant anomalies from uploaded images. 
The backend is built using FastAPI, providing a lightweight and high-speed API service that handles multi-part form data uploads, performs model inference, and returns structured JSON coordinate and confidence details. On the frontend, a responsive Next.js dashboard built with React and TypeScript delivers a seamless user experience, allowing users to upload leaf photos, adjust confidence thresholds, and view instant bounding box overlays and diagnostic suggestions directly on their screen.
## Key Features
* *Real-time Disease Detection:* Upload an image of a plant leaf and instantly detect diseases and pests with bounding box localizations.
* *Custom YOLOv8 Integration:* Uses a highly accurate YOLOv8 object detection model explicitly trained for agricultural anomalies.
* *Interactive Tweakable Parameters:* Users can adjust Confidence and IoU (Intersection over Union) thresholds dynamically via the UI to control detection sensitivity.
* *Modern Dashboard:* A sleek, dark-mode Next.js UI providing clear diagnostic suggestions and high-speed image rendering.
* *High-Performance API:* The FastAPI backend ensures low latency image inference and scalable API architecture for third-party integrations.
## Tech Stack
* *Frontend:* Next.js, React.js, TypeScript, Tailwind CSS
* *Backend & API:* FastAPI, Python, Uvicorn
* *Deep Learning & Computer Vision:* YOLOv8 (Ultralytics), PyTorch, Pillow, OpenCV
## System Flowchart
mermaid
graph TD
    A[User / Frontend Interface] -->|Uploads Leaf Image| B(Next.js Client)
    B -->|Multipart Form-Data Request| C{FastAPI Backend}
    C -->|Reads & Validates Image| D[Pillow / OpenCV Processing]
    D --> E((YOLOv8 Model Inference))
    E -->|Calculates Bounding Boxes & Confidences| F{Post-processing / NMS}
    F -->|Constructs JSON Response| C
    C -->|Returns API Response| B
    B -->|Renders UI & Bounding Boxes| A

## Setup & Installation
### 1. Backend Setup
bash
cd backend

bash
python -m venv venv

bash
venv\Scripts\activate

bash
pip install -r requirements.txt
uvicorn main:app --reload --port 8000

### 2. Frontend Setup
bash
cd frontend
npm install
npm run dev

The frontend will be available at http://localhost:3000 and the API documentation at http://localhost:8000/docs.
