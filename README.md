# AI-Powered Face Authentication & Attendance System 🤖📸

An innovative, zero-shot facial verification and liveness detection system that leverages advanced multimodal large language models (LLMs) to automate attendance tracking. By replacing traditional face embedding pipelines with holistic **Vision-to-Text analysis**, this system delivers real-time authentication, challenge-response anti-spoofing, and centralized attendance monitoring.

---

## 🚀 Core Features & Approach

### 1. Zero-Shot Face Verification
Unlike traditional systems relying on specialized embeddings (e.g., FaceNet, dlib), this architecture utilizes **Google's Gemini Multimodal Engine** to perform 1:N matching. Registered user images are evaluated within the model's context window against a "Live" camera feed through holistic structural and visual feature analysis.

### 2. Challenge-Response Liveness Detection
To prevent static photo bypasses, the system employs a dynamic challenge-response mechanism. Users are prompted to perform random physical micro-actions (e.g., *Blink*, *Smile*), which are validated in real-time by the visual model.

### 3. Spoof Prevention
The core vision engine is explicitly prompted to detect standard presentation attack indicators, including:
* **Screen Moiré Patterns** (from digital displays)
* **Depth Discrepancies** (flat paper/photo vs. 3D face)
* **Environmental Lighting Anomalies** ---

## 🛠️ System Architecture & Tech Stack

- **Core Engine:** Google Gemini Multimodal API (Vision-to-Text Analysis)
- **Computer Vision Pipeline:** OpenCV (Frame capturing & preprocessing)
- **Frontend Dashboard:** React, TypeScript, Tailwind CSS
- **Backend Service:** Node.js, Express, Python (API integration & prompt orchestration)

---

## 📈 Performance & Capabilities

* **Face Matching Accuracy:** `~90-95%` under standard, well-lit environments.
* **Liveness Detection:** Robust validation on overt facial state transitions (smiling, blinking).
* **System Latency:** `1-3 seconds` per verification cycle (bound primarily by API network round-trip time).
* **Training Footprint:** **Zero.** The system requires no explicit fine-tuning or specialized weights, relying entirely on advanced prompt engineering and foundation model generalization.

---

## ⚠️ Limitations & Failure Modes

Before deploying this system, please consider the following probabilistic biometric limitations:
* **Extreme Lighting:** High backlighting or low-lux environments significantly degrade visual feature extraction.
* **Context Scaling Window:** Designed for smaller groups/demos ($N < 10$). Scaling to enterprise-level user databases requires wrapping a vector search database (e.g., Pinecone, Milvus) around traditional embeddings prior to LLM validation.
* **Advanced Deepfakes:** While resilient against print and screen presentation attacks, high-fidelity generative deepfakes may bypass visual analysis without hardware-level depth sensors (IR/LiDAR).
* **Probabilistic Trade-offs:** This system is optimized for high user convenience (low False Rejection Rate), which may inherently result in a higher False Acceptance Rate compared to dedicated hardware biometric scanners.

---

## 🔧 Getting Started

### Prerequisites
* Python 3.10+
* Node.js v18+
* Gemini API Key (configured in your `.env`)
* A functional RGB Webcam
