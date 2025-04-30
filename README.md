Here’s a well-structured `README.md` for your Kinyarwanda Voice Assistant project, using appropriate markdown tags for clarity and documentation best practices:

---

```markdown
# 🗣️ Kinyarwanda Voice Assistant

A bilingual voice assistant built with [Whisper](https://github.com/openai/whisper) for speech-to-text and [TTS](https://github.com/coqui-ai/TTS) for text-to-speech, supporting Kinyarwanda Q&A and voice synthesis. It features an interactive [Gradio](https://www.gradio.app/) interface with two main modes: voice assistant and custom text-to-speech (TTS).

---

## 🔧 Features

- 🎙️ **Speech Recognition** using OpenAI Whisper.
- 💬 **Kinyarwanda Q&A** using predefined text responses.
- 🔊 **Text-to-Speech** using Hugging Face's `TTS` API.
- 🖥️ **Interactive Interface** using Gradio Tabs.
- 🔁 **Speaker Voice Transfer** (using reference audio).
- 🌐 **Web UI Launch with Sharing Option**.

---

---

## 🛠️ Installation & Setup

### ⚙️ Python Environment

Install dependencies in your Python environment or Jupyter notebook (e.g., Colab):

```bash
pip install -q openai-whisper
pip install numpy==1.24.3 --force-reinstall
pip install gradio
pip install transformers
pip install torchaudio
pip install TTS
pip install nemo-toolkit
```

> You can also install all required packages with:

```bash
pip install --no-cache-dir -r /content/drive/MyDrive/kinya-assistant/stt/requirements.txt
```

### 🧰 System Dependencies (for SoX audio tools)

```bash
apt-get update && apt-get install -y sox libsox-fmt-all
```

---

## 🚀 How to Use

### 🎤 Voice Assistant

- Upload your audio file or record directly.
- The system:
  - Transcribes audio using Whisper.
  - Matches text to pre-defined Kinyarwanda questions.
  - Responds using TTS and plays the audio back.

### 📢 Text-to-Speech

- Enter your desired text.
- Provide a WAV file as a reference speaker.
- Choose a language (`` supported).
- Synthesized speech will be generated and played back.

---

## 🧠 Code Overview

### Load Whisper & TTS Models

```python
whisper_model = whisper.load_model("small")
hf_model = TTS(model_name="tts_models/en/ljspeech/tacotron2-DDC")
```

### Transcribe Audio

```python
def transcribe_audio(audio_path):
    waveform, sample_rate = torchaudio.load(audio_path)
    ...
    result = whisper_model.transcribe(temp_audio_path)
    ...
```

### Text-to-Speech Synthesis

```python
def text_to_speech(text, speaker_wav, language):
    hf_model.tts_to_file(text=text, file_path="text_response.wav", ...)
```

### Gradio Interfaces

- **Voice Assistant Tab**
- **Text-to-Speech Tab**

Launched via:

```python
app.launch(share=True, debug=True)
```

---

## 📚 Predefined Q&A Dictionary

Example Kinyarwanda responses:

```python
qa_dict = {
    "amakuru yawe": "Nari meza, murakoze kubaza!",
    "wiriwe": "Nari meza, urakomeye?",
    "amafaranga angahe": "Mfite amafaranga 1000 RWF",
}
```

---

## 📦 Dependencies

- `openai-whisper`
- `numpy==1.24.3`
- `gradio`
- `transformers`
- `torchaudio`
- `TTS`
- `nemo-toolkit`
- `sox` (system)

---

## 🤝 Acknowledgements

- [OpenAI Whisper](https://github.com/openai/whisper)
- [Coqui TTS](https://github.com/coqui-ai/TTS)
- [Gradio](https://github.com/gradio-app/gradio)

---
