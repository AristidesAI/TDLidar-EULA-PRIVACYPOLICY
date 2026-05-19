## Troubleshooting

### 🍏 macOS

- **"uv: command not found" in Setup log** → `brew install uv` in Terminal, then click Install again.
- **"different Team IDs" error in Terminal when testing `python3.11 -c "import onnxruntime"`** → expected and harmless. TD's standalone Python is stricter than TouchDesigner.app itself. The libs load fine inside TD.
- **No mic input / `audio_buffer` is silent** → System Settings → Privacy & Security → Microphone → enable TouchDesigner.
- **`install_deps.sh: Operation not permitted`** → Terminal `chmod +x install_deps.sh` once, or use the Install pulse from inside the TOX (no shell needed).
- **Gatekeeper warns about the zip** → right-click → Open, or `xattr -d com.apple.quarantine ~/Downloads/SupertonicTOX-v1.0-slim.zip` in Terminal.
- **Apple Silicon (M1/M2/M3/M4)** → fully supported, uses CoreML by default. Intel Macs work too on CPU mode.

### 🪟 Windows

- **"uv is required" in Setup log** → `winget install --id=astral-sh.uv -e` in PowerShell, or `irm https://astral.sh/uv/install.ps1 | iex`. Then click Install again.
- **`install_deps.bat` won't run / SmartScreen blocks it** → right-click → Properties → "Unblock" → OK. Or run `install_deps.ps1` directly from a PowerShell prompt with `-ExecutionPolicy Bypass`.
- **No mic input** → Windows Settings → Privacy & security → Microphone → enable for desktop apps (or specifically TouchDesigner).
- **"TouchDesigner Python not found"** → if you installed TD in a non-default location, edit `install_deps.ps1` line ~16 to add your path to `$candidates`.
- **Antivirus flags the install** → onnxruntime + whisper.cpp DLLs are unsigned open-source binaries; whitelist the `vendor/` folder.
- **Windows on ARM (Surface Pro X / Snapdragon laptops)** → not tested. Should work via x86 emulation but expect slower inference. CoreML provider is Mac-only, so use CPU mode.

### Both platforms

- **No sound coming out** → wire the TOX's `out_audio` (first output) into an `Audio Device Out CHOP` and confirm the Out CHOP's `play` is on. The wrong output is `out_wave` — that's the static viz buffer, not playable streaming audio.
- **Live mode shows "LIVE (listening)" but never transcribes** → check **Current Mic RMS** on the STT page while you talk. It should spike well above the **VAD RMS Threshold**. If it doesn't, lower the threshold (try 0.005) or boost mic input gain.
- **Cuts off mid-sentence** → raise **Merge Grace** to 1.2–1.8s on the STT page.
- **First Generate takes 5+ seconds** → that's the one-time model load. Subsequent ones are ~1s. Click **Load Model** on the TTS page after install to pre-warm.
- **`ModuleNotFoundError: onnxruntime` (or `pywhispercpp`)** → Install pulse didn't finish or `vendor/` is missing. Re-run Install, then click **Re-init After Install**.
- **Old text plays after changing Text param** → fixed in v1.0 — if you see it, re-import the TOX.
