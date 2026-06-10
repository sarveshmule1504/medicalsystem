# 🏥 Arogya Vision - Smart Medical Waste Management System

**AI-Powered Automated Medical Waste Segregation**

An intelligent medical waste bin system designed to automate the segregation of medical waste into color-coded categories (sharps, biohazards, chemicals, and general waste). This project enhances medical facility sanitation standards through real-time AI-powered waste classification and automated sorting using computer vision and IoT integration.

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![Flask](https://img.shields.io/badge/Flask-Web%20Framework-green.svg)](https://flask.palletsprojects.com/)
[![ESP32](https://img.shields.io/badge/ESP32--CAM-Hardware-orange.svg)](https://www.espressif.com/en/products/socs/esp32)
[![License](https://img.shields.io/badge/License-Educational-brightgreen.svg)](#-license)
[![Status](https://img.shields.io/badge/Status-Active%20Development-blue.svg)](#)

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation & Setup](#-installation--setup)
- [Configuration](#-configuration)
- [Hardware Setup](#-hardware-setup-esp32-cam)
- [Usage](#-usage)
- [API Documentation](#-api-documentation)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌟 Features

### AI & Computer Vision
- 🤖 **AI-Powered Waste Classification** — Uses Google Gemini API for real-time waste identification
- 📸 **Real-Time Image Recognition** — Analyzes waste items as they're deposited
- 🎯 **Multi-Category Support** — Automatically categorizes into:
  - 🔴 **Sharps** (needles, syringes) → Puncture-proof containers
  - 🟡 **Biohazards** (infectious waste) → Yellow bins
  - 🟢 **Chemicals** (pharmaceutical waste) → Green bins
  - ⚫ **General Waste** → Black bins

### Hardware Integration
- 🔧 **Servo Motor Control** — Automated flap routing to correct bins
- 📡 **ESP32-CAM Integration** — Wireless image capture and sensor monitoring
- 🌐 **LoRa Communication** — Long-range IoT connectivity (optional)
- 📊 **Real-Time Sensor Monitoring** — Track bin fill levels and status

### Web Interface & Monitoring
- 📊 **Responsive Dashboard** — Monitor bin status in real-time
- 📈 **Classification History** — Track all waste items processed
- 🔔 **Alert System** — Notifications for full bins or system issues
- 📱 **Mobile-Friendly UI** — Works on desktops, tablets, and phones

### Deployment & Scalability
- ☁️ **Cloud-Ready** — Pre-configured `Procfile` for Heroku/Render deployment
- 🚀 **WSGI Compliant** — Production-ready server setup
- 🔐 **Secure API Integration** — Environment variable management for API keys

---

## 🛠️ Tech Stack

| Layer | Technologies |
|-------|--------------|
| **Backend** | Python 3.8+, Flask |
| **Frontend** | HTML5, CSS3, JavaScript |
| **Hardware** | C++ (Arduino IDE), ESP32-CAM, Servo Motors |
| **AI/ML** | Google Generative AI (Gemini API) |
| **IoT Communication** | WiFi, LoRa (optional) |
| **Deployment** | Procfile, Gunicorn, Heroku/Render |
| **Database** | SQLite (optional), CSV logging |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────┐
│          Web Dashboard (HTML/CSS/JavaScript)            │
└──────────────────────┬──────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────┐
│    Flask Backend (Python)                               │
│  ├─ Image Processing                                    │
│  ├─ API Endpoints                                       │
│  └─ Hardware Communication                              │
└──────────┬──────────────────────────────┬───────────────┘
           │                              │
    ┌──────▼──────┐            ┌──────────▼──────┐
    │  Gemini API │            │  ESP32-CAM      │
    │  (AI Model) │            │  (Image Capture)│
    └─────────────┘            └──────────┬──────┘
                                          │
                        ┌─────────────────▼──────────────┐
                        │ Servo Motors & Sensors         │
                        │ (Automated Sorting)            │
                        └────────────────────────────────┘
```

---

## 📂 Project Structure

```
medicalsystem/
│
├── medical_dustbin/                 ← Main application folder
│   ├── app.py                       ← Flask application entry point
│   ├── requirements.txt             ← Python dependencies
│   ├── .env.example                 ← Environment variables template
│   │
│   ├── templates/                   ← HTML templates
│   │   ├── index.html              ← Dashboard
│   │   ├── history.html            ← Classification history
│   │   └── settings.html           ← System settings
│   │
│   ├── static/                      ← CSS, JavaScript, Images
│   │   ├── css/
│   │   │   └── style.css
│   │   ├── js/
│   │   │   ├── dashboard.js
│   │   │   └── api.js
│   │   └── images/
│   │
│   ├── hardware/                    ← ESP32-CAM & Servo code
│   │   └── esp32_cam_sketch.ino    ← Arduino sketch
│   │
│   └── utils/                       ← Helper functions
│       ├── waste_classifier.py     ← AI classification logic
│       ├── servo_controller.py     ← Hardware control
│       └── logger.py               ← Logging utilities
│
├── README.md                        ← This file
├── Procfile                         ← Cloud deployment config
└── .gitignore
```

---

## 📋 Prerequisites

### Software Requirements
- **Python** 3.8 or higher
- **pip** (Python package manager)
- **Node.js** (optional, for advanced frontend tooling)
- **Arduino IDE** (for ESP32 development)
- **Git** (for cloning the repository)

### Hardware Requirements (Optional)
- **ESP32-CAM Module** — For automated image capture
- **Servo Motors** — For automated bin routing (2-4 units)
- **Webcam/USB Camera** — Alternative to ESP32-CAM
- **Power Supply** — 5V/2A for ESP32-CAM

### API & Credentials
- **Google Generative AI API Key** — Required for waste classification
  - Sign up at: https://ai.google.dev

---

## 💻 Installation & Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/sarveshmule1504/medicalsystem.git
cd medicalsystem
```

### Step 2: Set Up Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate it
# On Windows:
venv\Scripts\activate

# On Linux/macOS:
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
cd medical_dustbin
pip install -r requirements.txt
```

**Key Dependencies:**
- Flask — Web framework
- google-generativeai — Gemini API client
- python-dotenv — Environment variable management
- opencv-python — Computer vision
- Pillow — Image processing
- requests — HTTP library

### Step 4: Configure Environment Variables

1. **Create a `.env` file** in the `medical_dustbin/` directory:

```bash
cp .env.example .env
```

2. **Edit `.env`** and add your API key:

```env
# Google Gemini API Configuration
GEMINI_API_KEY=your_api_key_here
GEMINI_MODEL=gemini-1.5-flash

# Flask Configuration
FLASK_ENV=development
FLASK_APP=app.py
DEBUG=True

# Hardware Configuration
ESP32_IP=192.168.1.100
ESP32_PORT=8080

# Application Settings
LOG_LEVEL=INFO
MAX_UPLOAD_SIZE=10485760  # 10MB
```

### Step 5: Run the Application

```bash
python app.py
```

The application will start at: **http://localhost:5000**

---

## ⚙️ Configuration

### Waste Classification Settings

Edit `utils/waste_classifier.py` to customize waste categories and confidence thresholds:

```python
WASTE_CATEGORIES = {
    "sharps": {
        "bin_color": "red",
        "servo_position": 0,
        "keywords": ["needle", "syringe", "blade"]
    },
    "biohazard": {
        "bin_color": "yellow",
        "servo_position": 90,
        "keywords": ["blood", "infectious", "contaminated"]
    },
    "chemical": {
        "bin_color": "green",
        "servo_position": 180,
        "keywords": ["chemical", "pharmaceutical", "drug"]
    },
    "general": {
        "bin_color": "black",
        "servo_position": 270,
        "keywords": ["paper", "plastic", "general"]
    }
}

# Classification confidence threshold (0.0 - 1.0)
CONFIDENCE_THRESHOLD = 0.75
```

### Hardware Settings

Edit `utils/servo_controller.py` for motor control:

```python
# Servo Motor Configuration
SERVO_PIN = 12              # GPIO pin for servo
SERVO_FREQUENCY = 50        # Hz
SERVO_MIN_DUTY = 25         # Min pulse width
SERVO_MAX_DUTY = 125        # Max pulse width
SERVO_CALIBRATION = 90      # Neutral position
```

---

## 🔧 Hardware Setup (ESP32-CAM)

### Prerequisites
- ESP32-CAM module with OV2640 camera
- USB-UART adapter (CH340 or similar)
- Micro-USB cable
- Servo motor(s)
- Connecting wires

### Installation Steps

1. **Install ESP32 Board Manager in Arduino IDE:**
   - Go to **File → Preferences**
   - Add to "Additional Boards Manager URLs":
     ```
     https://dl.espressif.com/dl/package_esp32_index.json
     ```
   - Go to **Tools → Board Manager**
   - Search for "esp32" and install

2. **Open the Arduino Sketch:**
   ```
   hardware/esp32_cam_sketch.ino
   ```

3. **Configure WiFi & Server:**
   ```cpp
   const char* ssid = "Your_WiFi_SSID";
   const char* password = "Your_WiFi_Password";
   const char* serverIP = "192.168.1.X";  // Your Flask server IP
   const int serverPort = 5000;
   ```

4. **Select Board & Port:**
   - **Tools → Board → ESP32 Wrover Module**
   - **Tools → Port → COM# (CH340)**
   - **Tools → Upload Speed → 921600**

5. **Upload the Sketch:**
   - Click **Upload** button
   - Wait for compilation and upload

6. **Verify Connection:**
   - Open **Tools → Serial Monitor**
   - Set baud rate to 115200
   - Check for WiFi connection logs

---

## 🚀 Usage

### Starting the System

```bash
# Activate virtual environment
source venv/bin/activate  # Linux/macOS
# OR
venv\Scripts\activate     # Windows

# Run Flask app
python app.py
```

### Accessing the Dashboard

Open your web browser and navigate to:
```
http://localhost:5000
```

### Main Dashboard Features

- **📊 Real-Time Stats** — Current bin status and fill levels
- **📸 Live Camera Feed** — View waste being classified
- **📋 Classification Log** — History of all waste items
- **⚙️ System Settings** — Configure thresholds and categories
- **🔔 Alerts** — Notifications for critical events

### Testing Waste Classification

1. Use the test endpoint:
   ```bash
   curl -X POST http://localhost:5000/api/test-classify \
     -F "image=@test_image.jpg"
   ```

2. View classification results in the dashboard

---

## 🔌 API Documentation

### Core Endpoints

#### 1. **Classify Waste** (POST)
```http
POST /api/classify
Content-Type: multipart/form-data

Parameter: image (file)

Response:
{
  "status": "success",
  "category": "sharps",
  "confidence": 0.95,
  "bin_number": 1,
  "timestamp": "2026-06-10T10:30:00Z"
}
```

#### 2. **Get Bin Status** (GET)
```http
GET /api/bins/status

Response:
{
  "bins": [
    {
      "id": 1,
      "category": "sharps",
      "fill_level": 65,
      "last_update": "2026-06-10T10:30:00Z"
    },
    ...
  ]
}
```

#### 3. **Get Classification History** (GET)
```http
GET /api/history?limit=50&date=2026-06-10

Response:
{
  "total": 150,
  "items": [
    {
      "id": 1,
      "category": "biohazard",
      "confidence": 0.92,
      "timestamp": "2026-06-10T10:30:00Z"
    },
    ...
  ]
}
```

#### 4. **Control Servo** (POST)
```http
POST /api/servo/control
Content-Type: application/json

{
  "position": 90,
  "servo_id": 1
}

Response:
{
  "status": "success",
  "servo_id": 1,
  "current_position": 90
}
```

---

## 🐛 Troubleshooting

| Issue | Cause | Solution |
|-------|-------|----------|
| **GEMINI_API_KEY not found** | Environment variable not set | Create `.env` file with API key |
| **ESP32 not connecting** | WiFi credentials wrong | Verify SSID/password in sketch |
| **Camera not detected** | USB driver missing | Install CH340 drivers |
| **Servo not moving** | GPIO pin conflict | Check pin configuration in `servo_controller.py` |
| **Flask won't start** | Port 5000 in use | Change `app.run(port=8000)` in `app.py` |
| **Poor classification accuracy** | Low confidence threshold | Lower `CONFIDENCE_THRESHOLD` in config |
| **Slow image processing** | Large image size | Reduce upload limit in `.env` |
| **CORS errors** | Frontend/backend mismatch | Enable CORS in Flask app |

### Debug Mode

Enable verbose logging:

```bash
export FLASK_DEBUG=1
export LOG_LEVEL=DEBUG
python app.py
```

Check logs in: `logs/application.log`

---

## 📊 Performance Metrics

### Expected Performance
- **Classification Speed** — 0.5–2 seconds per image
- **Accuracy Rate** — 85–95% depending on image quality
- **Throughput** — 100+ items/hour per unit
- **Response Time** — <200ms API latency

### Optimization Tips
1. Use lower image resolution for faster processing
2. Increase `FRAME_SKIP` for real-time video
3. Implement image caching for repeated items
4. Use GPU acceleration (CUDA) if available

---

## 🤝 Contributing

We welcome contributions to improve medical waste management! 

### How to Contribute

1. **Fork the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/medicalsystem.git
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Commit your changes**
   ```bash
   git commit -m "Add amazing feature"
   ```

4. **Push to branch**
   ```bash
   git push origin feature/amazing-feature
   ```

5. **Open a Pull Request**

### Contribution Areas
- 🐛 **Bug Fixes** — Report and fix issues
- ✨ **Features** — Suggest and implement new features
- 📚 **Documentation** — Improve guides and API docs
- 🎨 **UI/UX** — Enhance dashboard design
- ⚡ **Performance** — Optimize code and algorithms
- 🧪 **Testing** — Add unit and integration tests

---

## 📄 License

This project is for **educational and research purposes only**.

---

## 🔗 Additional Resources

- [Google Generative AI Documentation](https://ai.google.dev/docs)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [ESP32 Documentation](https://docs.espressif.com/projects/esp-idf/en/latest/)
- [OpenCV Tutorials](https://docs.opencv.org/master/)

---

## 📞 Support & Issues

- 📋 **Report Bugs** — [Open an Issue](https://github.com/sarveshmule1504/medicalsystem/issues)
- 💬 **Discussions** — [Start a Discussion](https://github.com/sarveshmule1504/medicalsystem/discussions)
- 📧 **Contact** — via GitHub Issues

---

## 👨‍💻 Author

**Sarvesh Mule** — [GitHub Profile](https://github.com/sarveshmule1504)

---

## 🌟 Star & Follow

If this project helps you, please consider:
- ⭐ Starring this repository
- 👀 Following for updates
- 📢 Sharing with others interested in medical waste management

---

## 🎯 Roadmap

- [ ] Database integration (PostgreSQL)
- [ ] Real-time analytics dashboard
- [ ] Mobile app for remote monitoring
- [ ] Multiple unit coordination
- [ ] Predictive maintenance alerts
- [ ] Energy consumption tracking
- [ ] Cost analysis reports
- [ ] AI model fine-tuning with custom dataset

---

*Built with ❤️ to improve medical facility sanitation standards*

**Last Updated:** June 2026
