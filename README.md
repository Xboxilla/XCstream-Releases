# XCstream v0.9.9-beta — private binary releases

Current release: [XCstream v0.9.9-beta](https://github.com/Xboxilla/XCstream-Releases/releases/tag/v0.9.9-beta).
Source commit: `eed993ed0385de63c9b381a64ebde64a717c734b`.
643 tests passed, 0 failed, 0 skipped. See RELEASE.md and BUILD-MANIFEST.json.
The frozen v0.9.8-beta release remains available unchanged.
This repository contains native binary releases and distribution documentation
only: no XCstream source files or source history. Binary repository access does
not grant access to the separate private source repository.

Choose the native executable or optional ZIP matching your OS/CPU and verify
SHA256SUMS. ZIPs additionally carry third-party notices. Six targets:
Linux AMD64/ARM64, macOS AMD64/ARM64 and Windows AMD64/ARM64.
The release BUILD.json covers all six targets; each ZIP also carries its own
BUILD.json. Raw Unix downloads may need `chmod +x` before launch.

No Python/Docker runtime required. FFmpeg and ffprobe are not included.
Supply the qualified matching tools; default paths are bin/ffmpeg and
bin/ffprobe beside the executable (.exe on Windows), not PATH.

Linux AMD64 launch example:

```sh
chmod +x XCstream-0.9.9-beta-linux-amd64
./XCstream-0.9.9-beta-linux-amd64 --setup
./XCstream-0.9.9-beta-linux-amd64 --headless --config /path/to/XCstream.json \
  --ffmpeg-path /path/to/ffmpeg --ffprobe-path /path/to/ffprobe
```

Default JSON is XCstream.json beside the executable. Use writable log/buffer/
cache locations and trusted-network listeners. Kernel Media Server Direct and
standalone M3U share XCstream's normal tuner pool. See KERNEL-MEDIA-SERVER.md.
macOS is not Developer ID signed/notarized; trusted private downloads may need
Privacy & Security approval. Windows may likewise warn about unsigned apps.

First interactive launch without valid JSON enters terminal setup, saves
atomically, then waits for Enter before starting. Standard M3U/Both setup shows
media-server URLs before that pause; Direct-only shows Dashboard/Direct URLs. Explicit
--setup edits, saves and exits. Headless launch never prompts. Setup Ctrl-C
cancels cleanly with exit 130. Runtime SIGINT/SIGTERM use owned cleanup and exit
130/143, including harmless repeated signals. Startup endpoint discovery is
disk-log-only, never runtime terminal/HUD/Recent Events output.

Setup now provides a compact terminal-native interface, Unicode/ASCII fallback,
aligned values, grouped Review, and Back navigation. Interactive Review pauses
between complete sections when needed for terminal height: Enter/Space continues,
Q returns. Fitting and non-interactive Reviews do not pause. No browser or full-screen
TUI is required. Full setup groups HDHomeRun compatibility under Tuners; all
integrations still share one tuner pool. Local M3U/XMLTV files only.

DVR Priority is the default; Live TV Priority applies faster settings to the
same engine, with Custom derived from the actual values. Advanced exposes 19
expert controls. Matched synthetic Slate is generated asynchronously and reused
by media contract for this process lifetime; fixed H.264/HEVC Slate stays ready.
Protected Slate Handoff is optional and disabled by default. When enabled,
Slate remains public until private recovery proves sustained transport/media
progress, an exact compatible profile and an independently decodable IDR/config
start. Unsupported or unproven candidates remain private; see release limitations.

Logging/display controls: HUD and Web refresh intervals are 1–5 seconds (default
1); HUD Recent Events rows are 4–50 (default 10); Web rows are 10–100 (default
20). The dashboard and embedded view share Web preferences. First-run verbose
diagnostics starts off for new configurations only; existing values remain.

No license or redistribution grant is added. Python executable packaging is not
encryption or protection from reverse engineering.
