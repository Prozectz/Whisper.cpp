# Whisper.cpp WebAssembly Demo

A high-memory WebAssembly implementation of OpenAI's Whisper speech-to-text model running entirely in your browser.

## 🚀 Live Demo

**[Try it now!](https://your-username.github.io/whisper-demo)** *(Update this URL after deploying)*

## Features

- ✅ **Large File Support**: Process audio files up to 30 minutes (vs 1 minute in low-memory builds)
- ✅ **High Memory**: 512MB initial, 2GB maximum memory allocation
- ✅ **Multiple Formats**: Support for .wav, .mp3, .mp4, .m4a, .ogg, .webm
- ✅ **Download Results**: Save transcriptions with timestamps
- ✅ **Microphone Recording**: Record directly from your microphone
- ✅ **Multiple Models**: Support for tiny, base, small models and quantized versions
- ✅ **No Server Required**: Runs entirely in your browser

## Quick Start

### Option 1: Use GitHub Pages (Recommended)
1. Fork this repository
2. Enable GitHub Pages in repository settings
3. Visit your GitHub Pages URL
4. Start transcribing!

### Option 2: Host Locally
1. **Clone and serve:**
   ```bash
   git clone https://github.com/your-username/whisper-demo.git
   cd whisper-demo
   python -m http.server 8000
   ```
   
2. **Visit:** http://localhost:8000

3. **Load a model:** Click one of the model buttons (recommended: base.en)

4. **Upload audio:** Select your audio file (max 30 minutes)

5. **Transcribe:** Click "Transcribe" and wait for results

## Files

- `index.html` - Main demo page with enhanced UI
- `main.js` - High-memory WebAssembly build (1.4MB, official build)
- `helpers.js` - Utility functions
- `coi-serviceworker.js` - Required for SharedArrayBuffer support
- `samples/jfk.wav` - Sample audio file for testing

## Technical Details

This demo uses the official high-memory build with:
- **Memory Limits**: 512MB initial, 2GB maximum  
- **Function Signature**: 5-parameter Module.full_default()
- **Audio Limit**: 30 minutes (28.8M samples at 16kHz)
- **Threading**: 8 threads for faster processing
- **WebAssembly**: Single-file build with embedded WASM

## Comparison with Official Demo

This implementation matches the capabilities of the official demo at https://ggml.ai/whisper.cpp/ with the same memory limits and processing power, plus additional features like:
- Enhanced UI with better model management
- Download functionality for transcriptions
- Improved error handling
- Progress indicators

## Browser Compatibility

- ✅ **Chrome/Chromium**: Full support
- ✅ **Firefox**: Full support  
- ✅ **Safari**: Full support
- ✅ **Edge**: Full support
- ⚠️ **Mobile**: Limited (large memory requirements)

**Requirements:**
- WASM SIMD support (available in all modern browsers)
- SharedArrayBuffer support (enabled automatically via service worker)

## Performance Notes

- **First Load**: May take 10-30 seconds to download and initialize model
- **Processing Speed**: ~2-3x real-time on modern computers
- **Memory Usage**: Up to 2GB for large files
- **File Size Limits**: 30 minutes max audio length

## Development

Want to modify or rebuild? See the original repository for source code and build instructions:
- Source: [ggml-org/whisper.cpp](https://github.com/ggml-org/whisper.cpp)
- Build guide: See `examples/whisper.wasm/` in the source repo

## License

This project uses the same license as whisper.cpp.

## Credits

- [OpenAI Whisper](https://github.com/openai/whisper) - Original model
- [whisper.cpp](https://github.com/ggml-org/whisper.cpp) - C++ implementation
- [Emscripten](https://emscripten.org/) - WebAssembly compilation
