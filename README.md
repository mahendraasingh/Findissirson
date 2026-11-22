# Missing Person Identification System

An AI-powered web application for reporting, managing, and identifying missing persons using facial recognition. Built with Python, Streamlit, MediaPipe, Scikit-learn, and SQLite.

## Overview
The Missing Person Identification System helps locate missing individuals by matching public sighting reports with registered missing person cases. When a sighting photo or video is submitted, the system extracts facial landmarks and uses machine learning to match against open cases, notifying complainants when matches are found.

## Features
- Case Registration: Register missing persons with photo, personal details, and last known location.
- Public Sighting Portal: Submit sightings through photos or video without requiring an account.
- Facial Recognition Matching: Extracts 468-point 3D facial landmark mesh vectors using MediaPipe and matches cases using KNN.
- Interactive Map: Visualizes case distribution and density across cities using Folium.
- Email Notifications: Sends alert emails to complainants when a sighting matches a case.
- Role-Based Access: Admin and Officer access roles.

## Tech Stack
- Frontend: Streamlit
- Computer Vision: MediaPipe, OpenCV, Scikit-learn
- Database: SQLModel, SQLite
- Mapping: Folium, Streamlit-Folium
- Authentication: streamlit-authenticator, Bcrypt

## Prerequisites
- Python 3.11
- Git

## Installation
1. Clone the repository:
   git clone https://github.com/mahendraasingh/Findissirson.git
   cd Findissirson

2. Create and activate a virtual environment:
   python -m venv .venv
   # Windows:
   .venv\Scripts\activate
   # Linux / macOS:
   source .venv/bin/activate

3. Install required packages:
   pip install -r requirements.txt

## Configuration
Create a login_config.yml file in the project root with your user credentials:

credentials:
  usernames:
    admin:
      name: Admin User
      email: admin@example.com
      city: Delhi
      area: Sector 1
      role: Admin
      password: '<bcrypt_hashed_password>'
    officer:
      name: Officer User
      email: officer@example.com
      city: Delhi
      area: Sector 2
      role: Officer
      password: '<bcrypt_hashed_password>'
cookie:
  name: missing_person_auth
  key: secret_cookie_key
  expiry_days: 30

### Optional: Email Settings
Set the following environment variables to enable email alerts:
- SMTP_HOST
- SMTP_PORT
- SMTP_USER
- SMTP_PASSWORD

## Running the Application
- Admin & Officer Portal:
  streamlit run Home.py
  Open http://localhost:8501

- Public Sighting Portal:
  streamlit run mobile_app.py --server.port 8502
  Open http://localhost:8502

## License
MIT License
