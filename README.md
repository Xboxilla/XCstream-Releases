# XCstream v0.9.10-beta

Private binary distribution. No XCstream application source is included.
Current release: [XCstream v0.9.10-beta](https://github.com/Xboxilla/XCstream-Releases/releases/tag/v0.9.10-beta).
Download the matching native ZIP and SHA256SUMS from that private release.
See RELEASE.md for the actual six-platform verification matrix and the retained
failed Intel-on-Rosetta test; native Intel CI media qualification passed.
XCstream is a standalone live MPEG-TS continuity/recovery engine, not a DVR,
guide authority, or HLS/DASH server. Kernel Media Server Direct is optional.

## Install and run

Download the ZIP matching your operating system and processor. Check SHA256SUMS
before extracting. Keep the executable, `bin`, documentation and notices together.
Linux packages also require their included `_internal` runtime directory; do not
move the executable out of its extracted folder. This single-process bundle avoids
an extra signal-forwarding launcher during terminal cancellation and service stop.
The ZIP includes the matching Jellyfin FFmpeg/ffprobe pair; Python and Docker are
not required. Linux requires glibc 2.35 or newer and a system font usable by
Fontconfig (for example Ubuntu's `fonts-dejavu-core`).

Example Linux AMD64:

```sh
chmod +x XCstream-0.9.10-beta-linux-amd64 bin/ffmpeg bin/ffprobe
./XCstream-0.9.10-beta-linux-amd64
```

macOS uses `./XCstream-0.9.10-beta-darwin-arm64` (or `darwin-amd64`).
Windows uses `.\XCstream-0.9.10-beta-windows-amd64.exe` (or `windows-arm64.exe`).
These are unsigned beta binaries. After checking provenance and checksums, macOS
may require approval in System Settings → Privacy & Security; Windows may display
SmartScreen. Do not disable system security globally.

First interactive launch guides initial configuration, validates before saving,
and waits for Enter to launch. `--setup` opens the full terminal management utility
and saves/exits. Configuration defaults to XCstream.json beside the executable.
Use a writable installation/config directory. There is no browser configuration UI.
Standard M3U and Both modes require a readable local M3U file; XMLTV is optional.
Direct-only requires neither. All integrations share the same tuner pool.

For service/plugin use:

```sh
./XCstream-0.9.10-beta-linux-amd64 --headless --config /path/XCstream.json
```

Headless mode never prompts. SIGINT/SIGTERM request owned cleanup. Run as a
dedicated user, allow a graceful shutdown interval, and keep listeners on a trusted
network. `/dashboard` provides runtime visibility; `/kms` is the compact embedded
view. Standalone endpoints are `/playlist.m3u` and `/epg.xml`.

## Media tools and storage

Automatic discovery tries the installation's adjacent `bin` pair first, then
supported installed locations and PATH. Each candidate receives the application's
functional H.264/HEVC, AAC, MPEG-TS, probing and decoding qualification. Explicit
paths must be supplied as a pair using JSON `ffmpeg_path`/`ffprobe_path`, environment
`XC_FFMPEG_PATH`/`XC_FFPROBE_PATH`, or `--ffmpeg-path`/`--ffprobe-path`.
CLI overrides are not saved. Explicit incompatible tools fail rather than silently
falling back. Successful discovery does not require replacing the bundled tools.

Configuration precedence is explicit CLI > environment > JSON > built-in defaults.
Common environment overrides include XC_M3U_PATH, XC_XML_PATH,
XC_KMS_DIRECT_ENABLED and XC_AVAILABLE_TUNERS.
Persistent Slate assets and generated publications use the application's per-user
data location; tuner rings use the configured bounded buffer location.
Custom Slate video is optional; keep its configured local file available.

See RELEASE.md for qualification limits, KERNEL-MEDIA-SERVER.md for the Direct
contract, and notices for third-party licenses/source information. BUILD.json
records the exact source commit, native architecture and bundled media-tool hashes.
These beta builds are not a claim of production/DVR/client certification.
