# whisper.cpp/examples/stream-voice-type

This example is based on `examples/stream` and keeps the same single-file layout with minimal deltas.
The `whisper-stream-voice-type` tool behaves like `whisper-stream` and adds an optional global
start/stop toggle hotkey: **Ctrl+Alt+S**.

```bash
./build/bin/whisper-stream-voice-type -m ./models/ggml-base.en.bin -t 8 --step 500 --length 5000 --global-key-start-stop
```

Without `--global-key-start-stop`, behavior matches the regular stream example.

## Notes

- The global hotkey implementation in this example currently targets Linux/X11.
- Use `Ctrl+C` to quit.
