
# 🏥 Smart Medical Waste Management System (Arogya Vision)

An AI-powered smart medical waste bin system designed to automate the segregation of medical waste into color-coded categories (sharps, biohazards, chemicals, and general waste). This project enhances the safety of sanitation workers and ensures proper hazardous material disposal using computer vision and IoT hardware.

## 🌟 Key Features
* **AI-Powered Waste Classification:** Utilizes computer vision and the Gemini API to automatically identify and categorize medical waste in real-time.
* **Automated Sorting:** Integrates with hardware (servo motors) to automatically route waste into the correct bins (e.g., puncture-proof containers for sharps, yellow bins for biohazards).
* **Hardware Integration:** Communicates seamlessly with ESP32-CAM modules for image capture and sensor monitoring.
* **Web Dashboard:** A responsive HTML/web frontend to monitor bin status, classifications, and system health.
* **Cloud-Ready:** Configured with a `Procfile` for easy deployment to cloud platforms like Heroku or Render.

## 🛠️ Tech Stack
* **Backend:** Python (Flask)
* **Frontend:** HTML, CSS, JavaScript
* **Hardware/IoT:** C++ (ESP32-CAM, Servo Motors, LoRa communication)
* **AI Integration:** Google GenAI API for image analysis and classification
* **Deployment:** `Procfile` configured for WSGI server deployment

## 📂 Project Structure
* `medical_dustbin/`: Contains the core application files, including backend scripts, AI logic, and hardware communication protocols.
* `README.md`: Project documentation.
*(Note: As you push more code, this structure will expand to show `templates/`, `static/`, and hardware sketch folders.)*

## 💻 Local Setup & Installation

Follow these steps to run the software backend on your local machine:

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/sarveshmule1504/medicalsystem.git](https://github.com/sarveshmule1504/medicalsystem.git)
   cd medicalsystem/medical_dustbin

```

2. **Set up a virtual environment (Recommended):**
```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

```


3. **Install dependencies:**
Ensure you have a `requirements.txt` file in your directory, then run:
```bash
pip install -r requirements.txt

```


4. **Configure Environment Variables:**
You will need API keys for the AI classification to work.
* Create a `.env` file in the root directory.
* Add your Google Gemini API key: `GEMINI_API_KEY=your_api_key_here`


5. **Run the application:**
```bash
python app.py  # Or whatever your main Flask script is named

```



## ⚙️ Hardware Setup (ESP32-CAM)

1. Open the `.ino` / C++ files in the Arduino IDE.
2. Ensure you have the ESP32 board manager installed.
3. Update the WiFi credentials and the local IP address of your Flask server in the C++ code.
4. Flash the code to your ESP32-CAM module.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome to help improve medical sanitation standards! Feel free to check the [issues page](https://github.com/sarveshmule1504/medicalsystem/issues).

```

*** **Quick Tip:** If your main Python file is named something other than `app.py` (like `main.py`), make sure to update the "Run the application" command in step 5!

```
