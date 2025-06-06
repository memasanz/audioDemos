# Audio Demos

A collection of Python notebooks demonstrating real-time audio capture and transcription using Azure OpenAI services.

## Overview

This repository contains demonstrations of real-time audio processing capabilities, including:

- **Real-time audio capture** from microphone using PyAudio
- **Real-time speech transcription** using Azure OpenAI's GPT-4o mini transcribe model
- **WebSocket-based streaming** for low-latency audio processing
- **Voice Activity Detection (VAD)** for automatic speech detection
- **Audio preprocessing** with noise reduction capabilities

## Features

- 🎙️ **Live Audio Capture**: Capture audio directly from your microphone
- 🔗 **WebSocket Streaming**: Real-time audio streaming to Azure OpenAI
- 📝 **Live Transcription**: Instant speech-to-text conversion
- 🎤 **Voice Activity Detection**: Automatic detection of speech start/stop
- 🔇 **Noise Reduction**: Built-in audio preprocessing for better accuracy
- ⚡ **Low Latency**: Optimized for real-time applications

## Prerequisites

Before running the demos, ensure you have:

- **Python 3.7+** installed
- **Azure OpenAI subscription** with access to the real-time API
- **Microphone** connected to your computer
- **Audio drivers** properly configured on your system

### System Requirements

- **macOS/Linux**: PortAudio development headers
- **Windows**: Microsoft Visual C++ Build Tools (for PyAudio compilation)

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/memasanz/audioDemos.git
   cd audioDemos
   ```

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   
   For full functionality:
   ```bash
   pip install -r requirements.txt
   ```
   
   For WebSocket-only demos:
   ```bash
   pip install -r requirements_for_webs.txt
   ```

4. **Install system dependencies**:
   
   **macOS**:
   ```bash
   brew install portaudio
   ```
   
   **Ubuntu/Debian**:
   ```bash
   sudo apt-get install portaudio19-dev python3-pyaudio
   ```
   
   **Windows**: PyAudio should install with pip, but you may need Visual Studio Build Tools.

## Configuration

### Environment Variables

Create a `.env` file in the project root with your Azure OpenAI credentials:

```env
# Azure OpenAI Configuration
AZURE_OPENAI_GPT4O_API_KEY=your_api_key_here
AZURE_OPENAI_GPT4O_ENDPOINT=https://your-resource.openai.azure.com/
AZURE_OPENAI_GPT4O_DEPLOYMENT_ID=your_deployment_id
AZURE_OPENAI_STT_TTS_ENDPOINT=https://your-resource.openai.azure.com/
```

### Azure OpenAI Setup

1. **Create an Azure OpenAI resource** in the Azure portal
2. **Deploy the GPT-4o mini model** with transcription capabilities
3. **Note your endpoint URL and API key**
4. **Ensure real-time API access** is enabled for your subscription

## Usage

### Running the Audio Capture Demo

1. **Start Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```

2. **Open the main demo**:
   - Navigate to `01_AudioCapture.ipynb`
   - Run all cells in sequence

3. **Test the audio capture**:
   - The notebook will start recording from your microphone
   - Speak into the microphone
   - Watch real-time transcription appear in the output

### Expected Output

When running the demo, you should see output like:
```
🎙️ Recording started...
🔗 WebSocket connection established
Speak into the microphone...
🎤 Speech Detected
📥: Hello
📥:  world
📥: !
📨: Hello world!
🔇Speech Stopped
```

## Project Structure

```
audioDemos/
├── README.md                           # This file
├── requirements.txt                    # Full dependencies
├── requirements_for_webs.txt          # WebSocket-only dependencies
├── 01_AudioCapture.ipynb              # Main audio capture demo
├── 02_AudioCapture-SpeechToText.ipynb # (Coming soon)
├── 03_AudioCapture.ipynb              # (Coming soon)
├── speech.mp3                         # Sample audio file
└── .gitignore                         # Git ignore rules
```

## File Descriptions

### Notebooks

- **`01_AudioCapture.ipynb`**: Main demonstration of real-time audio capture and transcription using Azure OpenAI WebSocket API. Includes voice activity detection and audio streaming.

- **`02_AudioCapture-SpeechToText.ipynb`**: Placeholder for additional speech-to-text demonstrations.

- **`03_AudioCapture.ipynb`**: Placeholder for extended audio processing examples.

### Dependencies

- **`requirements.txt`**: Complete dependency list including:
  - `gradio`: Web UI framework for demos
  - `openai`: OpenAI Python client with voice helpers
  - `pyaudio`: Audio capture and playback
  - `websockets`: WebSocket client for real-time communication
  - `python-dotenv`: Environment variable management

- **`requirements_for_webs.txt`**: Minimal dependencies for WebSocket-only functionality.

### Audio Files

- **`speech.mp3`**: Sample audio file for testing (MPEG Layer III, 24 kHz, Mono).

## Troubleshooting

### Common Issues

**PyAudio Installation Error**:
```bash
# macOS
brew install portaudio
pip install pyaudio

# Ubuntu/Debian
sudo apt-get install portaudio19-dev
pip install pyaudio
```

**Microphone Not Working**:
- Check system audio settings
- Verify microphone permissions
- Test with other audio applications

**WebSocket Connection Failed**:
- Verify Azure OpenAI credentials in `.env`
- Check internet connectivity
- Ensure real-time API is enabled

**No Audio Detected**:
- Check microphone input levels
- Adjust VAD threshold in the configuration
- Verify audio format compatibility

### Audio Configuration

The demo uses these audio settings:
- **Format**: 16-bit PCM
- **Sample Rate**: 24 kHz
- **Channels**: Mono
- **Frame Size**: 1024 samples

You can adjust these in the notebook configuration section.

## API Configuration

The Azure OpenAI configuration includes:
- **Model**: `gpt-4o-mini-transcribe`
- **Audio Format**: `pcm16`
- **VAD Threshold**: 0.5
- **Silence Duration**: 500ms
- **Noise Reduction**: Near-field optimization

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for:
- Additional audio processing demos
- Bug fixes and improvements
- Documentation updates
- New features and capabilities

## License

This project is for demonstration purposes. Please ensure compliance with Azure OpenAI terms of service when using the real-time API.

## Support

For issues related to:
- **Azure OpenAI**: Check the [Azure OpenAI documentation](https://docs.microsoft.com/en-us/azure/cognitive-services/openai/)
- **PyAudio**: See the [PyAudio documentation](https://pypi.org/project/PyAudio/)
- **This repository**: Open an issue on GitHub

---

**Note**: This is a demonstration project. For production use, consider implementing proper error handling, security measures, and rate limiting.