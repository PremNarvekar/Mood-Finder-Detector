Mood Finder Detector — MERN Full-Stack (JavaScript + Face API.js)

Mood Finder Detector is a full-stack MERN application that analyzes a user’s mood in real-time using Face API.js and AI-driven scoring.
The app uses your webcam to detect facial expressions, run them through a mood engine, and present a clean UI dashboard showing the user’s emotional state.

This project is built entirely with JavaScript, keeping the code simple, flexible, and beginner-friendly while still being scalable for real production use.

📸 App Preview

🔥 Tech Stack — MERN + Face API.js
Frontend – React + Vite

React (JavaScript)

Vite for instant HMR & fast builds

Face API.js integrated directly in the client

TailwindCSS or normal CSS supported

Webcam live mood tracking UI

Mood result dashboard

Backend – Node.js + Express

REST APIs for user login, history & settings

Stores mood results, timestamps, analytics

JWT-based authentication

Clean middleware-driven structure

Database – MongoDB (Mongoose)

Stores user profiles

Facial emotion history

Daily / weekly mood analytics

Fast + scalable NoSQL operations

AI / Detection Layer – Face API.js

Facial landmark detection

Emotion detection (happy, angry, sad, neutral, surprised, fearful, disgust)

Real-time face tracking

Browser-based — no heavy GPU needed

🎯 Features
✔ Real-time mood detection

Uses Face API.js + your camera to detect:

Happiness

Sadness

Anger

Fear

Disgust

Surprise

Neutral

✔ Mood scoring algorithm

Your expression weights are converted into:

Mood score

Mood title

Mood color theme

Suggestions or reactions

✔ Mood History

Backend stores:

Timestamp

Detected mood

Expression confidence

✔ Clean MERN architecture

A simple, scalable layout:

root/
│
├── client/ (React + Vite)
│   ├── src/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── pages/
│   │   ├── utils/
│   │   ├── faceapi/ (models + detection logic)
│   │   └── App.jsx
│   └── index.html
│
├── server/ (Node + Express)
│   ├── routes/
│   ├── controllers/
│   ├── models/
│   ├── middleware/
│   └── server.js
│
└── README.md

📦 Installation & Setup
1. Clone the repo
git clone your-repo-url
cd mood-finder-detector

2. Install frontend (React)
cd client
npm install

3. Install backend (Node.js)
cd ../server
npm install

4. Run Face API models

Face API needs downloadable models.
Create this folder:

client/src/faceapi/models/


Add these models inside:

face_expression_model-weights

face_landmark_68_model-weights

face_recognition_model-weights

tiny_face_detector_model-weights

(If you want, I can generate the download links too.)

5. Start development
Frontend
npm run dev

Backend
npm run server

📡 API Endpoints
POST /api/mood/save

Saves a detected mood entry.

GET /api/mood/history

Returns user’s mood history.

POST /api/auth/register

Create new user.

POST /api/auth/login

User login with JWT.

🎥 Face API Integration Example (Frontend)
import * as faceapi from 'face-api.js';

export const loadModels = async () => {
  await faceapi.nets.tinyFaceDetector.load('/models/');
  await faceapi.nets.faceExpressionNet.load('/models/');
  await faceapi.nets.faceLandmark68Net.load('/models/');
};

export const detectMood = async (videoElement) => {
  const detection = await faceapi
    .detectSingleFace(
      videoElement,
      new faceapi.TinyFaceDetectorOptions()
    )
    .withFaceExpressions();

  return detection?.expressions || null;
};

👤 User Flow

Open the app → camera activates

Face API runs detection

Mood score calculated

Result displayed in real-time

User logs in → mood history synced

Backend analytics unlocks deeper insights

🔒 Security

CORS handled

JWT token-based auth

Secure cookies (optional)

Sanitized inputs

Production-ready Express config

🚀 Roadmap Suggestions

👤 Profile-based mood trends

🌙 Mood-based UI theme switching

🎧 Voice tone analysis (optional)

🤖 AI suggestions for stress relief

📈 Weekly mood analytics

📱 React Native mobile app