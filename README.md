# 🗣️ AI_Language_Tutor — Voice-Driven AI Language Tutor

> Speak. Learn. Repeat. — A fully voice-driven language tutor powered by Groq LLaMA 3.3-70b and Whisper, running in Google Colab.

---

## 📌 Overview

**AI_Language_Tutor** is a real-time, voice-to-voice AI language tutor that listens to you speak, understands what you said, corrects your grammar, and replies back in audio — all in your target language. It runs entirely in Google Colab with no local setup required.

Built with:
- 🧠 **Groq LLaMA 3.3-70b** — fast, intelligent multilingual tutoring
- 🎙️ **Faster-Whisper (Medium)** — accurate speech-to-text transcription
- 🔊 **gTTS** — natural text-to-speech audio playback
- 🌐 **Web Audio API** — browser-based microphone recording via JavaScript

---

## ✨ Features

| Feature | Details |
|---|---|
| 🌍 Multilingual Support | Auto-detects and replies in your spoken language |
| 🎙️ Voice Input | Records audio directly in the browser via Colab |
| 🤖 AI Tutor | Politely corrects grammar, asks follow-up questions, encourages learners |
| 🔊 Voice Output | Converts AI replies to speech and autoplays them |
| ⚡ Fast Inference | Powered by Groq's low-latency API |
| 🧪 GPU Accelerated | Whisper runs on CUDA with float16 precision |

---

## 🛠️ Tech Stack

```
Speech Input       →   Web Audio API (JavaScript MediaRecorder)
Transcription      →   faster-whisper (medium, CUDA, float16)
Language Model     →   Groq API — LLaMA 3.3-70b-versatile
Language Detection →   langdetect
Text-to-Speech     →   gTTS (Google Text-to-Speech)
Runtime            →   Google Colab (GPU runtime recommended)
```

---

## 🚀 Getting Started

### 1. Open in Google Colab

Upload `AI_Language_Tutor.ipynb` to [Google Colab](https://colab.research.google.com/) and switch to a **GPU runtime**:

> `Runtime → Change runtime type → T4 GPU`

### 2. Set Your API Key

Add your Groq API key as a Colab secret:

> `🔑 Secrets (left panel) → Add new secret`
> - Name: `GROQ_API_KEY`
> - Value: `your_groq_api_key_here`

Get a free Groq API key at [console.groq.com](https://console.groq.com/).

### 3. Install Dependencies

Run the install cell:

```bash
pip install groq faster-whisper gtts langdetect
```

### 4. Run the Notebook

Execute cells top to bottom. When you reach the recording cell:
1. Allow microphone access when prompted by your browser
2. Speak clearly for up to 5 seconds
3. The AI tutor will transcribe, respond, and play back its reply

---

## 🔁 Pipeline

```
[Your Voice]
     │
     ▼
[Browser MediaRecorder] ──► input.webm
     │
     ▼
[faster-whisper (Whisper Medium)] ──► Transcribed Text
     │
     ▼
[Groq LLaMA 3.3-70b] ──► AI Tutor Reply (Text)
     │
     ▼
[gTTS + langdetect] ──► reply.mp3
     │
     ▼
[IPython Audio] ──► 🔊 Autoplay in Colab
```

---

## 📁 Project Structure

```
AI_Language_Tutor.ipynb   # Main notebook
input.webm                # Recorded audio (auto-generated)
reply.mp3                 # AI audio response (auto-generated)
```

---

## ⚙️ Configuration

You can tune the tutor's behaviour by editing the `SYSTEM_PROMPT` in the notebook:

```python
SYSTEM_PROMPT = """
You are a multilingual AI_Language_Tutor AI tutor.

Rules:
- Detect language automatically
- Reply in the same language
- Correct grammar politely
- Keep answers short
- Teach naturally
- Ask follow-up questions
- Encourage the learner
"""
```

Other configurable parameters:

| Parameter | Default | Description |
|---|---|---|
| `model` | `llama-3.3-70b-versatile` | Groq model to use |
| `temperature` | `0.7` | Response creativity |
| `max_tokens` | `300` | Max reply length |
| `beam_size` | `5` | Whisper transcription beam width |
| Recording duration | `5000ms` | Milliseconds of audio to capture |

---

## 🌐 Supported Languages

Macau auto-detects your language from speech. gTTS supports 65+ languages including:

`English` · `Hindi` · `Spanish` · `French` · `Mandarin` · `Arabic` · `Portuguese` · `German` · `Japanese` · `Korean` · `Italian` · `Russian` · and many more.

---

## ⚠️ Known Limitations

- Recording duration is fixed at 5 seconds per turn (can be extended in the JS snippet)
- Requires browser microphone permission in Colab
- GPU runtime required for Whisper's `float16` compute type
- gTTS requires an internet connection for TTS synthesis
- Stateless: conversation history is not maintained across turns

---

## 🔮 Roadmap

- [ ] Silence-detection-based recording (auto-stop when user stops speaking)
- [ ] Multi-turn conversation memory
- [ ] Edge-TTS neural voice support for higher quality audio
- [ ] Session scoring and level progression
- [ ] Progress tracking with matplotlib charts
- [ ] Support for structured lesson plans per language

---

## 👤 Author

**Utkarsh**
B.Tech Computer Science — Ajay Kumar Garg Engineering College (2027)
[GitHub](#) · [LinkedIn](#)

---

## 📄 License

This project is licensed under the MIT License. See `LICENSE` for details.

---

> *"The limits of my language mean the limits of my world." — Ludwig Wittgenstein*
