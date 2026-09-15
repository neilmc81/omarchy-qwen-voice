# Qwen Voice — Omarchy bar widget

A listening-state indicator for a [Qwen](https://qwenlm.github.io/) voice
assistant, as an Omarchy bar widget.

- **Green mic** — the assistant is listening
- **Dimmed mic** — muted or stopped
- **Left-click** toggles the assistant's microphone

## Requirements

- Omarchy (Quickshell-based shell with QML plugin support)
- The `qwen-voice-toggle.sh` companion script (toggles the mic, invoked on click)

## Installation

```bash
# 1. Clone the plugin into your Omarchy plugins directory
git clone https://github.com/neilmc81/omarchy-qwen-voice \
    ~/.config/omarchy/plugins/qwen.voice

# 2. Make sure qwen-voice-toggle.sh is installed at the path referenced in
#    VoiceIndicator.qml.

# 3. Register the widget in ~/.config/omarchy/shell.json (bar section),
#    then reload the shell:
#    omarchy restart shell
```

## How it works

The widget watches the JSON state file that `qwen-voice-toggle.sh` writes on
every microphone transition (live, no polling):

```
$XDG_RUNTIME_DIR/qwen-voice/state.json
{ "status": "listening" | "muted" | "stopped", "label": "..." }
```

Left-click runs the toggle script, which flips the mic and updates the state
file.

## Files

```
manifest.json        plugin metadata
VoiceIndicator.qml   bar icon + state handling
```

## License

[MIT](LICENSE)