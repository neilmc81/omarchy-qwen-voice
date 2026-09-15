# Qwen Voice — Omarchy bar widget

A listening-state indicator for the Qwen voice assistant, as an Omarchy bar
widget.

- **Green mic** (`󰍬`) when the assistant is listening.
- **Dimmed mic** (`󰍭`) when muted or stopped.
- **Left-click** toggles the assistant's microphone.

## How state gets in

The widget watchs the JSON state file that `qwen-voice-toggle.sh` writes on
every microphone transition (live, `FileView` + `watchChanges`, no polling):

    $XDG_RUNTIME_DIR/qwen-voice/state.json
    { "status": "listening" | "muted" | "stopped", "label": "..." }

## Files

- `VoiceIndicator.qml`  — the bar icon and state handling
- `manifest.json`      — plugin metadata

## Install

Registered in `~/.config/omarchy/shell.json` (bar). Requires the companion
`qwen-voice-toggle.sh` at
`~/.local/share/qwen-omarchy-control/bin/qwen-voice-toggle.sh`.