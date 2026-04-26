# Drishti AI

> AI-powered bilingual assistive system for the visually impaired with real-time speech interaction, image understanding, and contextual memory

Drishti is a full-stack multimodal AI system that integrates **speech recognition**, **computer vision**, **context-aware memory**, **bilingual interaction**, **real-time audio feedback**, and **edge-device deployment** — helping visually impaired users understand and interact with their surroundings independently.

---

## 🎯 Features

| Feature | Description |
|--------|-------------|
| 🎤 **Wake Word Activation** | Hands-free activation using "Hello Lens" (English) and "Namaste Lens" (Hindi) via offline Vosk engine |
| 🗣️ **Bilingual Speech Recognition** | Converts Hindi & English speech to text using Whisper with high noise robustness |
| 👁️ **Multimodal Understanding** | Captures images and uses GPT-4o-mini to describe scenes, objects, and text |
| 🧠 **Contextual Memory** | Maintains session-level summarized memory for follow-up queries |
| 🔊 **Text-to-Speech (TTS)** | Converts responses into natural speech for real-time audio feedback |
| ⚡ **Real-Time Interaction** | Low latency pipeline with device + backend hybrid architecture |
| 🌐 **API-based Backend** | Flask APIs process audio and image inputs efficiently |
| 📷 **Image Capture Pipeline** | OpenCV-based camera integration for real-time scene capture |
| 📡 **Session Management** | Uses session IDs to track and maintain conversational continuity |

---

## 🏗️ Architecture

### Tech Stack

| Layer | Technology |
|------|-----------|
| **Speech Recognition** | OpenAI Whisper (`whisper-small`) |
| **Multimodal AI** | GPT-4o-mini (text + image reasoning) |
| **Wake Word Detection** | Vosk (offline, low-latency) |
| **Backend** | Flask (Python) |
| **Computer Vision** | OpenCV |
| **Memory Engine** | Custom session-based summarization |
| **TTS** | Custom text-to-speech pipeline |
| **Hardware** | Radxa Zero 3W, I2S Mic, Pi Camera, Bluetooth Speaker |
| **Deployment** | Local device + backend server |

---

## 🔄 System Workflow
Wake Word Detection (“Hello Lens” / “Namaste Lens”)
│
▼
Speech Capture (Microphone)
│
▼
Speech → Text (Whisper)
│
├── If image required
│       ▼
│   Image Capture (Camera)
│       ▼
│   Vision Processing (GPT-4o-mini)
│
▼
Context Memory Update (Summary-based)
│
▼
Response Generation (GPT-4o-mini)
│
▼
Text → Speech (TTS)
│
▼
Audio Output (Speaker)

---

## 🧠 Memory System

Drishti uses a **lightweight memory mechanism** instead of storing full conversations.

- Stores **short summarized context**
- Maintains **session continuity using session_id**
- Enables follow-up queries like:
  - “What is the price?”
  - “Read that again”

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/checkSST` | Process audio input and return speech response |
| `POST` | `/checkWImage` | Process audio + image input |
| `POST` | `/upload` | Upload image for processing |

---

## ⚙️ Backend Components

| Module | Function |
|-------|---------|
| `sst()` | Converts speech to text using Whisper |
| `Summarize()` | Handles text queries + memory update |
| `SummarizeWI()` | Handles image + query processing |
| `CHAT_MEMORY` | Stores session summaries |
| `startPipeline()` | Generates final speech output |

---

## 🧪 Testing & Evaluation

| Parameter | Description |
|----------|-------------|
| 🎤 Wake Word Accuracy | Tested under noise and quiet environments |
| 🗣️ Speech Recognition | Hindi & English command accuracy |
| 👁️ Image Understanding | Object detection & text reading |
| 🧠 Context Retention | Multi-turn conversation validation |
| ⚡ Latency | Real-time response generation |

---

## 💰 Cost Analysis

| Component | Cost (INR) |
|----------|------------|
| Radxa Zero 3W | 2585 |
| Camera Module | 1025 |
| Microphone | 420 |
| Audio Module | 645 |
| SD Card | 530 |
| Misc + Shipping | ~1750 |
| **Total** | **~6960 INR** |

---

## 🚀 Quick Start

### Prerequisites
- Python 3.10+
- Internet connection (for AI models)
- Camera + Microphone

### Setup

```bash
git clone https://github.com/your-repo-link
cd drishti

pip install -r requirements.txt

python server.py 

#📁 Project Structure
drishti/
├── server.py              # Flask backend
├── main.py                # Pipeline execution
├── received_images/       # Image storage
├── models/                # AI models
├── utils/                 # Helper functions
├── requirements.txt
└── README.md

#🔒 Limitations

* Performance affected in noisy environments
* Requires internet for AI inference
* Limited language support (Hindi & English)

⸻

#🔮 Future Work

* 👓 Smart Glasses Integration
* ⚡ On-device AI processing
* 🌍 Multi-language support
* 📶 Offline vision capabilities

⸻

#📌 Conclusion

Drishti demonstrates how speech, vision, and memory AI can be combined into a practical and affordable assistive system.
It enables visually impaired users to interact with the world more independently through natural voice-based communication.

⸻

#👨‍💻 Team

* Kumar Ayush
* Deep
* Mayank Monu
* Anchal Jain

⸻

#🙏 Acknowledgement

Special thanks to Dr. Rahul Nijhawan for guidance and mentorship.

⸻

#⭐ If you like this project

Give it a star ⭐ on GitHub!
