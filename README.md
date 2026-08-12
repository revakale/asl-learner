# ASL Learner — American Sign Language Learning Platform

A desktop application that combines real-time sign-language detection with a
lesson/learning platform for American Sign Language (ASL).

## Overview

- **`main.py`** — Tkinter-based login and lesson management platform (student/teacher
  accounts, lesson upload, practice & demonstration recording, SQLite-backed user
  database). Launches the live detector as a subprocess.
- **`asl.py`** — PyQt5 real-time ASL hand-sign detector. Uses OpenCV + cvzone's
  `HandDetector` to track the hand and a Keras model to classify the sign, with
  text-to-speech (pyttsx3 / gTTS) and translation (`googletrans`) support.
- **`models/A.h5`** — Trained Keras model used for sign classification.
- **`demo/Project_Demonstration.mp4`** — Short demo of the app in action.
- **`assets/`** — Reference images (e.g. the ASL alphabet chart).

## Features

- Login / registration system for students and teachers (SQLite)
- Real-time webcam-based hand sign detection and text prediction
- Text-to-speech output of recognized signs
- Translation between languages via Google Translate
- Lesson upload, practice recording, and demonstration recording
- Spell-check / word suggestion (via `pyenchant`)

## Project structure

```
asl-learner/
├── main.py                 # Entry point — login & lesson platform
├── asl.py                  # Real-time ASL detector (launched by main.py)
├── models/
│   └── A.h5                # Trained classification model
├── demo/
│   └── Project_Demonstration.mp4
├── assets/
│   └── alphabet/            # ASL alphabet reference images (A.jpg – Z.jpg)
├── requirements.txt
└── README.md
```

## Setup

1. **Clone the repo**
   ```bash
   git clone https://github.com/<your-username>/asl-learner.git
   cd asl-learner
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate      # Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

   > Note: `pyenchant` requires the Enchant C library to be installed on your
   > system (on Windows this usually ships with the pip wheel; on Linux install
   > `libenchant-2-2` via your package manager). `PyAudio` may also need
   > `portaudio` installed on Linux/Mac before `pip install` succeeds.

4. **Run the app**
   ```bash
   python main.py
   ```
   The detector (`asl.py`) is launched automatically from within the app, and
   expects `models/A.h5` — update `MODEL_PATH` in `asl.py` if you move the model.

## Demo

See [`demo/Project_Demonstration.mp4`](demo/Project_Demonstration.mp4) for a
walkthrough of the app.

## Tech stack

Python · OpenCV · cvzone · Keras/TensorFlow · PyQt5 · Tkinter · SQLite · gTTS · pyttsx3 · googletrans

## License

Add a license of your choice (e.g. MIT) if you plan to make this repo public.
