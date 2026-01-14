# Fully-Local AI Smart Home Assistant – "Larry"

## Overview
Larry is a fully local AI-powered voice assistant built with Home Assistant, Whisper, Piper, and Ollama. Unlike cloud-based assistants like Alexa, everything runs locally, ensuring privacy and control over your smart home.

## Hardware Setup
- **Raspberry Pi 5** – runs Home Assistant & Piper (text-to-speech)
- **SeeedStudio 4-mic array** – voice input
- **USB speaker** – audio output
- **Linux server** – runs Whisper in Docker for speech-to-text

## Software Setup
- **Home Assistant** configured with:
  - Assist Microphone add-on
  - Custom wake word “Larry”
  - Ollama integration for conversation agent
- **Whisper** in Docker on Linux server
- **Piper** for TTS on Raspberry Pi
- **Ollama** running LLaMA 3.2 (local AI brain)

## Usage
1. Say the wake word **“Larry”**.  
2. Microphone captures audio → sent to Whisper for transcription.  
3. Ollama generates response → sent back to Piper.  
4. Piper plays the audio through USB speaker.  

Commands I use:
```bash
nohup ollama serve &
sudo systemctl restart ollama
watch -n 0.5 nvidia-smi
