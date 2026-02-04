# Fully-Local AI Smart Home Assistant – "Larry"

> A fully local AI voice assistant integrating Home Assistant, Whisper, Piper, and Ollama, built on a Raspberry Pi and Linux server to control smart home devices while ensuring complete privacy.

---

## Overview
Larry is a fully local AI-powered voice assistant. Unlike cloud-based assistants like Alexa, everything runs locally, ensuring privacy and full control over your smart home. Larry can understand spoken commands, generate responses via a local LLM (LLaMA 3.2), and execute smart home actions all without sending data to the cloud.

This project demonstrates distributed system integration, real-time audio processing, and AI orchestration on local devices.

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

## Audio Pipeline
[Mic Array] --> [Whisper Docker] --> [Ollama LLM] --> [Piper TTS] --> [USB Speaker]

---

## Usage
1. Say the wake word **“Larry”**.  
2. Audio is captured by the mic array → sent to Whisper for transcription.  
3. Ollama generates a response or executes Home Assistant commands.  
4. Piper converts the response to speech and plays it through the USB speaker.  

---

## Key Commands
```bash
# Run Ollama in background
nohup ollama serve &

# Restart Ollama via systemd
sudo systemctl restart ollama

# Monitor GPU usage for LLM
watch -n 0.5 nvidia-smi

```
## Troubleshooting & Lessons Learned
- **Ollama IP binding:** Had to set to 0.0.0.0 for network accessibility
- **Assist Device:** Must select "Larry" in Home Assistant dropdown
- **NAS issues:** Mounting configuration required adjustment
- **Latency:** Optimized Docker networking and audio pipeline to reduce delays

## Skills & Technologies
- **Languages & Tools:** Python, Docker, Bash, YAML, Linux
- **AI & ML:** Whisper (speech-to-text), Piper (TTS), Ollama (LLM, LLaMA 3.2)
- **Smart Home & IoT:** Home Assistant, custom wake words, mic array integration
- **Networking & Systems:** Distributed systems, Docker networking, GPU monitoring

## Achievements
- Built a fully local AI assistant, ensuring privacy and data control
- Integrated multiple AI services in a distributed system across Raspberry Pi and Linux server
- Optimized audio pipeline and Docker networking to reduce latency and improve responsiveness
- Troubleshot and resolved hardware/software issues in a complex IoT environment

