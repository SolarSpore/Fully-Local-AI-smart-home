# Fully-Local AI Smart Home Assistant – "Larry"

## Overview
Larry is a fully local AI-powered voice assistant built with **Home Assistant**, **Whisper**, **Piper**, and **Ollama**. Unlike cloud-based assistants like Alexa, everything runs locally, ensuring privacy and full control over your smart home. Larry can understand spoken commands, generate responses via a local LLM (LLaMA 3.2), and execute smart home actions — all without sending data to the cloud.

---

## Hardware Setup
- **Raspberry Pi 5** – runs Home Assistant & Piper (text-to-speech)  
- **SeeedStudio 4-mic array** – voice input  
- **USB speaker** – audio output  
- **Linux server** – runs Whisper in Docker for speech-to-text  

---

## Software Setup
- **Home Assistant** configured with:
  - Assist Microphone add-on  
  - Custom wake word **“Larry”**  
  - Ollama integration as conversation agent  
- **Whisper** running in Docker on a separate Linux server  
- **Piper** for text-to-speech on Raspberry Pi  
- **Ollama** serving **LLaMA 3.2** locally  

This distributed setup allows audio capture, transcription, response generation, and playback entirely on local devices.

---

## Usage
1. Say the wake word **“Larry”**.  
2. Audio is captured by the mic array → sent to Whisper for transcription.  
3. Ollama generates a response or executes Home Assistant commands.  
4. Piper converts the response to speech and plays it through the USB speaker.  

### Key Commands
```bash
# Run Ollama in background
nohup ollama serve &

# Restart Ollama via systemd
sudo systemctl restart ollama

# Monitor GPU usage for LLM
watch -n 0.5 nvidia-smi
