Requirements for EZ CorridorKey (hybrid / lean package)

System
┌─────────────────────────┬─────────────────────────────────────────────────────────────────────────┐
│ Requirement             │ Details                                                                 │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────┤
│ OS                      │ Windows 10/11 64-bit (this installer path is Windows-focused)           │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────┤
│ CPU                     │ Multi-core recommended (hybrid mode uses CPU + RAM heavily)             │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────┤
│ RAM                     │ 16 GB+ strongly recommended (8 GB minimum; hybrid uses a system RAM     │
│                         │ buffer)                                                                 │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────┤
│ GPU (optional but       │ NVIDIA with CUDA-capable drivers, or AMD (e.g. RX 580 4GB) via DirectML │
│ better)                 │                                                                         │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────┤
│ GPU VRAM                │ 4 GB+ usable on GPU path; low-VRAM tiling is used under ~10 GB          │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────┤
│ Disk                    │ ~2 MB for lean zip; several GB free after install (venv + models +      │
│                         │ FFmpeg)                                                                 │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────┤
│ Display                 │ Normal desktop UI (PySide6)                                             │
└─────────────────────────┴─────────────────────────────────────────────────────────────────────────┘

Software (required)
┌─────────────────┬─────────────────────────────────────────────────────────────────────────────────┐
│ Requirement     │ Details                                                                         │
├─────────────────┼─────────────────────────────────────────────────────────────────────────────────┤
│ Python          │ 3.10 – 3.13 (project pins <3.14) with Add to PATH                               │
├─────────────────┼─────────────────────────────────────────────────────────────────────────────────┤
│ pip / venv      │ Bundled with Python                                                             │
├─────────────────┼─────────────────────────────────────────────────────────────────────────────────┤
│ Internet        │ First install (packages), FFmpeg download, model downloads                      │
├─────────────────┼─────────────────────────────────────────────────────────────────────────────────┤
│ C++ Build Tools │ Often needed for packages like OpenEXR (installer can prompt for VS Build       │
│                 │ Tools)                                                                          │
└─────────────────┴─────────────────────────────────────────────────────────────────────────────────┘

Software (highly recommended)
┌─────────────┬───────────────────────────────────────────────────────────────────────────┐
│ Requirement │ Details                                                                   │
├─────────────┼───────────────────────────────────────────────────────────────────────────┤
│ FFmpeg      │ Not in lean zip — run installer\Download-FFmpeg.ps1 or put FFmpeg on PATH │
├─────────────┼───────────────────────────────────────────────────────────────────────────┤
│ Git         │ Useful for updates (3-update.bat)                                         │
├─────────────┼───────────────────────────────────────────────────────────────────────────┤
│ GPU drivers │ Latest NVIDIA or AMD drivers                                              │
└─────────────┴───────────────────────────────────────────────────────────────────────────┘

What gets installed after unzip (disk)
┌─────────────────────────────────────────────┬──────────────────────────────────────────────────┐
│ Component                                   │ Approx. size / note                              │
├─────────────────────────────────────────────┼──────────────────────────────────────────────────┤
│ Python venv + deps (PyTorch, PySide6, etc.) │ ~2–6+ GB depending on CUDA/CPU wheels            │
├─────────────────────────────────────────────┼──────────────────────────────────────────────────┤
│ CorridorKey core models                     │ ~700–800 MB+ via Install_CorridorKey_Windows.bat │
├─────────────────────────────────────────────┼──────────────────────────────────────────────────┤
│ BiRefNet / MatAnyone (if used)              │ Extra hundreds of MB                             │
├─────────────────────────────────────────────┼──────────────────────────────────────────────────┤
│ GVM / VideoMaMa (optional)                  │ Very large (multi‑GB; only if you install those) │
├─────────────────────────────────────────────┼──────────────────────────────────────────────────┤
│ FFmpeg essentials                           │ ~50–100 MB via download script                   │
└─────────────────────────────────────────────┴──────────────────────────────────────────────────┘

Optional
┌─────────────────────────────┬───────────────────────────────────────────────────────────────────┐
│ Optional                    │ Details                                                           │
├─────────────────────────────┼───────────────────────────────────────────────────────────────────┤
│ DaVinci Resolve             │ Only if using Resolve bridge scripts                              │
├─────────────────────────────┼───────────────────────────────────────────────────────────────────┤
│ NVIDIA CUDA toolkit/runtime │ For full CUDA speed (driver usually enough for many torch wheels) │
├─────────────────────────────┼───────────────────────────────────────────────────────────────────┤
│ torch-directml              │ For AMD hybrid (Install-Hybrid-GPU.bat tries this)                │
└─────────────────────────────┴───────────────────────────────────────────────────────────────────┘

Hybrid modes (what the PC needs)
┌────────────────┬───────────────────────────────────────────┐
│ Mode           │ Needs                                     │
├────────────────┼───────────────────────────────────────────┤
│ CUDA           │ NVIDIA GPU + working CUDA torch           │
├────────────────┼───────────────────────────────────────────┤
│ DirectML (AMD) │ AMD GPU + torch-directml + system RAM     │
├────────────────┼───────────────────────────────────────────┤
│ CPU            │ No dedicated GPU; lots of RAM/time (slow) │
└────────────────┴───────────────────────────────────────────┘

Env knobs (set by hybrid installer):
• CORRIDORKEY_DEVICE=auto|cuda|dml|cpu
• CORRIDORKEY_VRAM_GB (e.g. 4)
• CORRIDORKEY_RAM_BUFFER_GB (e.g. 8–16)
• CORRIDORKEY_OPT_MODE=lowvram
• CORRIDORKEY_HYBRID=1

Not required
• Bundled FFmpeg in the lean zip (download after)
• Pre-shipped AI weights in the lean zip (download after)
• Admin rights for a user install under %LOCALAPPDATA% (Build Tools install may need admin)

Practical minimum to actually key video
1. Windows 10/11
2. Python 3.10–3.13
3. ~16 GB RAM (or patience on less)
4. Internet for first setup
5. FFmpeg + CorridorKey model install after the lean zip
6. GPU optional but much better than CPU-only
