# 👁️ Ocularis AI
### *The Next-Gen Visual Perception Engine for Autonomous QA*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.11](https://img.shields.io/badge/python-3.11-blue.svg)](https://www.python.org/downloads/)
[![AI-Powered](https://img.shields.io/badge/AI-Vision--LLM-blueviolet)](https://langchain.com/)

Ocularis AI is a semantic visual regression framework designed to eliminate "false positives" in UI testing. By combining Computer Vision with Vision LLMs, Ocularis understands the *context* of a UI change rather than just the pixel difference.

## ✨ Key Features
- **Semantic Analysis:** Distinguishes between layout breaks (Critical) and dynamic content shifts (Ignore).
- **Auto-Healing Baselines:** AI suggests when a baseline is outdated due to a planned feature and offers to update it.
- **Cross-Platform Normalization:** Uses OpenCV to align images taken on different OS/Browser combinations.
- **Smart Masking:** Supply a list of CSS selectors to automatically ignore dynamic regions like clocks or ads.

## 🏗️ Architecture
Ocularis operates on a decoupled architecture using FastAPI and Redis. 
[View Detailed Architecture Documentation](./docs/architecture.md)

## 🚀 Getting Started

### Prerequisites
- Python 3.11+
- Docker & Docker Compose
- API Key (OpenAI or Google Gemini)

### Installation
```bash
git clone [https://github.com/your-profile/ocularis-ai.git](https://github.com/your-profile/ocularis-ai.git)
cd ocularis-ai
pip install -r requirements.txt
cp .env.example .env # Add your API keys here
```

### Usage
- Start the Ocularis service
```bash
docker-compose up -d
```
- Run a comparison
You can send a POST request to the API or use CLI
```bash
python ocularis-cli.py compare \
  --base ./baselines/home.png \
  --actual ./screenshots/home_run_01.png \
  --dom ./metadata/home_dom.json
```

### Sample AI Output
Ocularis Verdict: PASS (Soft Warning)
Reasoning: "A 3px vertical shift was detected in the 'Header' component. However, the 'Login' button remains fully visible and functional. The shift is likely due to font-rendering differences in the Linux environment. No regression detected."
