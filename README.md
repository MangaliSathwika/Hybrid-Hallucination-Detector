# 🛡️ Hybrid LLM Hallucination Detection System (HallucinationGuard)

A real-time AI trust center and multi-layered verification engine designed to evaluate the factual accuracy and semantic reliability of Large Language Model (LLM) responses.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.10%2B-brightgreen.svg)
![Status](https://img.shields.io/badge/status-Live-success.svg)

---

## 🌟 Overview

Large Language Models (LLMs) can generate convincing but factually incorrect or ungrounded responses ("hallucinations"). **HallucinationGuard** provides a production-grade verification console combining **semantic drift tracking**, **knowledge graph grounding**, and **factual entailment checking** to flag hallucinations and generate verified alternatives in real time.

---

## ✨ Key Features

- **Multi-Stage AI Entailment Pipeline**: Sequential animated pipeline tracking:
  $$\text{Input} \longrightarrow \text{Semantic Check} \longrightarrow \text{Fact Check} \longrightarrow \text{Consensus} \longrightarrow \text{Risk Score} \longrightarrow \text{Verdict}$$
- **Real-Time Circular Risk Gauge**: Animated SVG circular meter dynamically showing risk indices (e.g., High Risk / Flagged vs. Low Risk / Verified).
- **Dual Verification Details Cards**:
  - ⚠️ **Detected Issues**: Highlights inaccurate terms and timeline mismatches with visual flags.
  - ✓ **Verified Alternative**: Displays ground-truth verified responses with one-click copy functionality.
- **Knowledge Graph Citations**: Expandable sources drawer with verified reference nodes and SHA-256 validation signatures.
- **Pre-configured Benchmarking Presets**: Instant evaluation samples:
  - *Sample 1: Hallucinated History (Lincoln 1789)*
  - *Sample 2: False Geography (Sydney Capital)*
  - *Sample 3: Grounded Fact (Washington)*
- **Engine Parameter Controls**: Interactive modal for adjusting Hallucination Sensitivity, Semantic Similarity Weight, and Entailment Strictness.
- **Zero-Dependency Native Backend**: Lightweight Python backend with built-in CORS, health checks, and cross-platform compatibility.

---

## 🏗️ Architecture & Technology Stack

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Frontend** | HTML5, Modern CSS3, Vanilla JS | Ultra-clean, high-contrast, responsive UI with zero external UI framework dependencies |
| **Typography** | *Plus Jakarta Sans* & *JetBrains Mono* | Clean editorial readability and code/numerical precision |
| **Backend** | Python (`http.server`, `json`, `os`) | Native HTTP server with zero pip requirements |
| **API Protocol** | REST JSON (`POST /api/evaluate`) | Standardized request/response contract |
| **Deployment** | Render / Docker / Cloudflare Tunnel | Ready for immediate cloud hosting |

---

## 🚀 Quick Start (Local Setup)

### 1. Clone the Repository
```bash
git clone https://github.com/MangaliSathwika/Hybrid-Hallucination-Detector.git
cd Hybrid-Hallucination-Detector
```

### 2. Start the Backend Server
Because the backend uses standard Python libraries, no virtual environment or `pip install` is required:
```bash
python server.py
```

You should see:
```text
[SERVER] Active on port 5000 (http://127.0.0.1:5000 and http://localhost:5000)
[SERVER] Ready to receive traffic in your browser.
```

### 3. Open in Browser
Open your browser and navigate to:
👉 **`http://127.0.0.1:5000`**

---

## 📡 API Reference

### Evaluate Target Payload

- **Endpoint**: `/api/evaluate`
- **Method**: `POST`
- **Headers**: `Content-Type: application/json`

#### Request Body
```json
{
  "user_query": "Who was the first president of the United States and when did he take office?",
  "llm_response": "Abraham Lincoln was the first president of the United States. He took office in 1789 after winning the Revolutionary War.",
  "model_name": "Llama-3-8B (Local Node)"
}
```

#### Response Body
```json
{
  "score": 78,
  "status": "High Risk / Hallucinated",
  "highlighted_text": "🔴 <b>[Hallucination Detected]</b> <b>Abraham Lincoln</b> was flagged as incorrect based on historical reference grounding data.<br><br>🔴 <b>[Factual Anomaly]</b> Timeline mismatch: The year <b>1789</b> does not align with this president.",
  "corrected_response": "George Washington was the first president of the United States. He took office on April 30, 1789.",
  "sources": [
    "Reference DB: U.S. Executive Branch Archives",
    "Verified Knowledge Graph Node Lookup"
  ],
  "semantic_match": 85
}
```

### Health Check
- **Endpoint**: `/health`
- **Method**: `GET`
- **Response**: `{"status": "ok", "engine": "HallucinationGuard"}`

---

## ☁️ Deployment (Render.com)

1. Fork or push this repository to GitHub.
2. Sign in to **[Render.com](https://render.com/)** and click **New +** → **Web Service**.
3. Connect your **`Hybrid-Hallucination-Detector`** repository.
4. Set the following configuration:
   - **Runtime**: `Python 3`
   - **Build Command**: `echo "Build done"` *(or leave blank)*
   - **Start Command**: `python server.py`
5. Click **Deploy Web Service**.

Render will provision a free global HTTPS URL (e.g. `https://your-service.onrender.com`).

---

## 📁 Project Structure

```text
├── index.html        # Clean, modern white Trust Center frontend UI
├── server.py         # Native Python HTTP server handling /api/evaluate and /health
└── README.md         # Documentation
```

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
