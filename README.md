# 🚨 FirstHelp - Emergency Assistance Web Application

A comprehensive **first-aid assistance platform** with emergency SOS capabilities, CPR guidance, emergency scenarios guide, and automatic SMS alerting via Twilio integration.

## 🌟 Features

### 1. **Emergency SOS System** 🆘
- **Floating SOS button** - Always accessible
- **5-second countdown** - Prevents accidental activation
- **Automatic SMS** - Backend sends emergency message via Twilio
- **Call 911** - Direct emergency services
- **Emergency contact** - Call/SMS saved contacts
- **GPS location sharing** - Automatic location in messages
- **Fallback mechanism** - Browser SMS if backend unavailable

### 2. **CPR Emergency Timer** ⏱️
- **110 BPM audio metronome** - Correct compression rhythm
- **30:2 cycle tracking** - Standard CPR protocol
- **Visual progress indicators** - Real-time feedback
- **Start/Pause/Reset controls** - Easy operation
- **Compression counter** - Track progress

### 3. **User Registration & Profiles** 👤
- **Profile management** - Name, phone, email, emergency contact
- **Login/logout** - Secure profile display
- **Edit capabilities** - Update information anytime
- **Local storage** - Privacy-first data storage
- **Form validation** - Ensures correct data format

### 4. **Emergency Scenarios Guide** 📖
- **Multiple scenarios** - Heart attack, choking, burns, cuts, stroke
- **Symptom identification** - Visual and text guides
- **Step-by-step first aid** - Clear instructions
- **Image support** - Visual demonstration
- **Category filtering** - Easy navigation

### 5. **Modern UI/UX** 🎨
- **White & red theme** - Medical emergency aesthetic
- **Responsive design** - Works on all devices
- **Smooth animations** - Professional polish
- **Intuitive navigation** - Easy to use in emergencies
- **Accessibility** - Large touch targets for stress situations

---

## 🚀 Quick Start

### Prerequisites
- **Node.js** (v14 or higher)
- **npm** or **yarn**
- **Twilio account** (for automatic SMS - optional)

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/onkaravhad26/health-demo-1-.git
cd health-demo-1-
```

2. **Install dependencies:**
```bash
npm install
```

3. **Run the frontend:**
```bash
npm run dev
```

4. **Access the app:**
```
http://localhost:5173
```

---

## ⚙️ Backend Setup (Optional - for Automatic SMS)

### 1. Get Twilio Credentials

- Sign up: [https://www.twilio.com/try-twilio](https://www.twilio.com/try-twilio)
- Get **Account SID**, **Auth Token**, and a **Phone Number**
- Free trial: $15 credit (~500 SMS)

### 2. Configure Environment

Create `.env` file in the root directory:

```env
PORT=5000
NODE_ENV=development

TWILIO_ACCOUNT_SID=ACxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
TWILIO_AUTH_TOKEN=your_auth_token_here
TWILIO_PHONE_NUMBER=+1234567890
```

### 3. Run Backend Server

**Terminal 1 (Backend):**
```bash
npm run server:dev
```

**Terminal 2 (Frontend):**
```bash
npm run dev
```

---

## 📂 Project Structure

```
firsthelp/
├── src/
│   ├── App.jsx                # Main application component
│   ├── App.css                # Main styles
│   ├── EmergencySOS.jsx       # SOS system component
│   ├── EmergencySOS.css       # SOS styles
│   ├── CPRTimer.jsx           # CPR timer component
│   ├── CPRTimer.css           # CPR timer styles
│   ├── UserProfile.jsx        # User registration/profile
│   ├── UserProfile.css        # Profile styles
│   ├── EmergencyGuide.jsx     # Emergency scenarios guide
│   ├── EmergencyGuide.css     # Guide styles
│   ├── emergencyData.js       # Scenario data structure
│   ├── index.css              # Global styles
│   └── main.jsx               # Entry point
├── public/
│   └── assets/                # Emergency scenario images
├── server.js                  # Express backend with Twilio
├── .env.example               # Environment template
├── package.json               # Dependencies & scripts
└── README.md                  # This file
```

---

## 🎯 Usage Guide

### For Users

1. **Register Your Profile:**
   - Click "Login" → Fill registration form
   - Add emergency contact number
   - Save profile (stored locally)

2. **In an Emergency:**
   - Click the **🆘 button** (bottom-right)
   - 5-second countdown begins
   - **Automatic SMS sent** to emergency contact
   - Choose additional actions:
     - Call 911
     - Call emergency contact
     - Share location

3. **CPR Emergency:**
   - Click "🚨 CPR Emergency Timer" or Emergency Timer card
   - Press "Start Timer"
   - Follow 110 BPM audio rhythm
   - Complete 30:2 cycles

4. **Learn First Aid:**
   - Navigate to "Guide" section
   - Browse emergency scenarios
   - Read symptoms and first aid steps

---

## 🛠️ Technologies Used

### Frontend
- **React** - UI framework
- **Vite** - Build tool & dev server
- **CSS3** - Styling with animations
- **Geolocation API** - GPS location tracking
- **LocalStorage** - Client-side data persistence

### Backend
- **Node.js** - Runtime environment
- **Express** - Web framework
- **Twilio** - SMS API integration
- **CORS** - Cross-origin resource sharing
- **dotenv** - Environment configuration

---

## 📱 Features in Detail

### SOS System Architecture

**Frontend → Backend Flow:**
1. User activates SOS (5-second countdown)
2. Frontend calls `/api/send-sos` endpoint
3. Backend sends SMS via Twilio API
4. Emergency contact receives message with location
5. Fallback: Browser SMS if backend unavailable

**Message Format:**
```
🚨 EMERGENCY ALERT 🚨
From: [User Name]

I NEED HELP!

📍 Location:
Lat: [latitude]
Long: [longitude]
View on Map: [Google Maps link]

Time: [timestamp]

This is an automated emergency message from FirstHelp.
```

---

## 🔒 Privacy & Security

- **Local data storage** - Profile data stays on device
- **No external tracking** - Privacy-first approach
- **Secure Twilio** - Industry-standard SMS service
- **Environment variables** - Sensitive credentials protected
- **.gitignore** - Prevents credential commits

---

## 📊 API Endpoints

### Backend API

**Base URL:** `http://localhost:5000`

#### 1. Health Check
```http
GET /api/health
```

**Response:**
```json
{
  "status": "ok",
  "message": "FirstHelp Backend Server is running",
  "twilioConfigured": true
}
```

#### 2. Send SOS
```http
POST /api/send-sos
```

**Request Body:**
```json
{
  "userName": "John Doe",
  "emergencyContact": "+1234567890",
  "location": {
    "latitude": 37.7749,
    "longitude": -122.4194
  },
  "customMessage": ""
}
```

**Response:**
```json
{
  "success": true,
  "messageSid": "SMxxxxxxxxxxxxx",
  "sentTo": "+1234567890",
  "message": "SOS message sent successfully"
}
```

#### 3. Test SMS
```http
POST /api/test-sms
```

**Request Body:**
```json
{
  "phoneNumber": "+1234567890"
}
```

---

## ⚠️ Disclaimer

**FirstHelp is an emergency assistance tool and should NOT replace professional medical training or emergency services.**

- Always call 911 or local emergency services in life-threatening situations
- Use CPR timer only if trained in CPR
- First aid information is for guidance - seek professional medical help
- Test the system before relying on it in emergencies

---

## 🌟 Star this repo if you find it helpful!

Made with ❤️ for emergency preparedness

---

**Version:** 1.0.0  
**Last Updated:** February 2026  
**Status:** Active Development
