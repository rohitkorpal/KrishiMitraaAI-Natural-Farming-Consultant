# 🌾 Voice-Based Multilevel Natural Farming Consultant

A premium, interactive, AI-powered Streamlit web application designed as a voice-first mobile/desktop consultant for farmers transitioning to Zero Budget Natural Farming (ZBNF) and organic cultivation. 

This prototype fulfills the complete specifications of **Option B — Multilevel Natural Farming Consultant** for the interview assessment.

---

## 🌟 Key Features

1. **🎙️ Voice Assistant & Detailed Expert Q&A (AI-Powered)**
   - **Speech-to-Text (STT)**: Native `st.audio_input` browser integration captures clear voice commands.
   - **Direct Audio LLM Analysis**: Sends recorded audio files directly to the Google Gemini API (`gemini-flash-lite-latest`) for unified, low-latency transcription and comprehension.
   - **Text-to-Speech (TTS)**: Synthesizes high-quality audio responses in English and Hindi/Hinglish using `gTTS` and auto-plays them via Streamlit's native `st.audio(..., autoplay=True)`.
   - **Ask the Organic Expert**: Text-based detailed query search yielding step-by-step organic farming instructions.
   - **Real-Time Reset Widget Control**: Dynamic key counters clear recorded audio/response blocks instantly.

2. **🌾 Crop & Seed Guidance**
   - **Soil Prediction ML**: Utilizes a pre-trained **Random Forest Classifier** (`crop_recommendation_model.pkl`) to recommend the top 3 optimal crops based on N-P-K levels, temperature, humidity, pH, and expected rainfall.
   - **Organic Enrichment**: Enriches ML recommendations with organic/traditional seed varieties (e.g. *Pusa Basmati 1121*), sowing duration, and applicable government subsidies.
   - **🌱 AI Crop Plan Explainer**: One-click generation of customized soil prep, organic nutrient dosing schedules, and companion cropping plans via the Gemini API.

3. **🐛 Organic Disease Control (with AI Vision)**
   - **Traditional Lookup**: Instant remedies for 12+ major crop pests and diseases using traditional inputs (Neem oil, sour buttermilk, etc.).
   - **📸 AI Smart Leaf Diagnosis (Computer Vision)**: Image uploader where farmers upload leaf photos to get an instant disease diagnosis and natural organic remedies from Gemini Vision.

4. **🌦️ Weather & Market Intel**
   - **Weather Forecasts**: Fetches temperature and humidity for regional cities, with a smart offline mock data generator.
   - **Mandi Crop Prices**: Lists live-updating market price trends.
   - **📈 AI Mandi Price Analyser**: Triggers a detailed marketing analysis advising on holding/selling strategies, crop shifts, and processing value-addition (e.g., converting mustard to oil).

5. **📚 Natural Farming Academy**
   - Detailed guides on the **7-Layer Multilevel Canopy Cropping** model ( Coconut $\rightarrow$ Mango $\rightarrow$ Banana $\rightarrow$ Low Shrubs $\rightarrow$ Ground Cover $\rightarrow$ Root Crops $\rightarrow$ Climbers).
   - Preparation guides for traditional organic inputs (*Jeevamrutha*, *Beejamrutha*, *Agni Astra*).
   - Core pillars of ZBNF.

---

## 🛠️ Technology Stack
* **Frontend/Backend Framework**: Streamlit (v1.58.0)
* **LLM & Vision API**: Google Gemini API (`gemini-flash-lite-latest`)
* **Audio Processing (TTS)**: `gTTS` (Google Text-To-Speech)
* **Machine Learning**: Scikit-Learn, Joblib, NumPy, Pandas (Random Forest model)

---

## 🧠 System Prompt & Guardrails
To prevent recommending chemical pesticides or synthetic fertilizers, the LLM is wrapped in a strict instruction pipeline:
```text
You are a Voice-Based Multilevel Natural Farming Consultant.
Your instructions:
- Provide advice exclusively on natural and organic farming (Zero Budget Natural Farming / ZBNF).
- Suggest organic remedies such as Jeevamrutha, Beejamrutha, Agni Astra, Neem oil, sour buttermilk, companion planting, and crop rotation.
- NEVER suggest chemical fertilizers (e.g. Urea, DAP), chemical pesticides, or GMO seeds. 
- Keep responses short, concise, and direct (maximum 3-4 sentences) so they are suitable for speech synthesis (Text-to-Speech).
- Respond in the language of the query (English or Hindi/Hinglish).
```

---

## 📂 Project Directory Structure
```text
AgroSolution-main/
│
├── UI - Copy/
│   ├── models/
│   │   └── crop_recommendation_model.pkl    # Machine Learning Model
│   ├── .env                                  # Local Environment Keys (Gemini API)
│   ├── .gitignore                            # Excludes keys from GitHub
│   └── organic_consultant.py                 # Core Streamlit App Code
├── docs/
│   ├── prompt_design.md                      # Prompt Engineering Details
│   └── architecture.md                       # System Architecture Details
├── README.md                                 # Project Overview (This file)
└── LICENSE
```

---

## 🚀 Setup & Installation

1. **Clone the Repository**:
   ```bash
   git clone <repo-url>
   cd AgroSolution-main
   ```

2. **Install Dependencies**:
   ```bash
   pip install streamlit pandas numpy joblib requests gTTS
   ```

3. **Configure Environment Variables**:
   Create a `.env` file inside the `UI - Copy` directory:
   ```env
   GEMINI_API_KEY=your_google_gemini_api_key_here
   ```

4. **Launch the Application**:
   ```bash
   streamlit run "UI - Copy/organic_consultant.py" --server.port 8505
   ```
