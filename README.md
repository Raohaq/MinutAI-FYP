# MinutAI — AI Meeting Summariser (Final Year Project Artefact)

MinutAI is a web-based application that processes recorded meeting audio files and generates:
- a timestamped transcript
- a 3–5 sentence summary
- extracted action items (tasks + optional due dates)

Users must confirm meeting consent before processing. Results are saved per-user and can be viewed later in Meeting History.

---

## Tech Stack
**Web App:** ASP.NET Core Razor Pages (.NET 8)  
**Database:** SQLite (stores users + meeting outputs)  
**AI Pipeline:** Python  
- Transcription: faster-whisper (Whisper base model on CPU)  
- Summary + Action Items: local LLM using Ollama API  
- Audio processing: ffmpeg + ffprobe  

---

## Prerequisites
1) **.NET 8 SDK**  
2) **Python 3.10+** (3.11 recommended)  
3) **FFmpeg + FFprobe** installed and available in PATH  
   - `ffmpeg -version`
   - `ffprobe -version`
4) **Ollama** installed and running  
   - `ollama pull qwen2.5:3b-instruct`
   - `ollama serve`

---

## Project Structure (Top Level)
- `MinutAI.web/` → ASP.NET Razor Pages web app
- `backend/` → Python pipeline
- `outputs/` → generated output files (transcript/summary/action items)
- `test_audio/` or `demo_audio/` → optional demo files

---

## Setup (Python Backend)
Open PowerShell:

```powershell
cd "backend"
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r requirements.txt