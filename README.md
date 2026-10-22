# XCstream v0.9.10-beta — Proprietary Beta

XCstream is a standalone live-stream continuity and MPEG-TS recovery engine.
It is not a DVR, guide authority, or HLS/DASH server. Kernel Media Server Direct
is optional. No XCstream application source is included.

Copyright © 2026 Eyal Benedek. All rights reserved.
See [LICENSE-XCSTREAM.md](LICENSE-XCSTREAM.md) for evaluation and distribution
terms. Third-party components retain their own licenses.

Current release: [XCstream v0.9.10-beta](https://github.com/Xboxilla/XCstream/releases/tag/v0.9.10-beta).
Download the matching native ZIP and SHA256SUMS. See [RELEASE.md](RELEASE.md)
for the six-platform qualification matrix and documented limitations.

## Install and run

Verify the ZIP against SHA256SUMS before extracting. Keep the executable, `bin`,
documentation, license and notices together. Linux packages also require their
included `_internal` runtime directory; do not move the executable out of its
extracted folder. The ZIP includes the matching Jellyfin FFmpeg/ffprobe pair;
no separate Python installation or Docker environment is required. Linux
requires glibc 2.35 or newer and a system font usable by Fontconfig, such as
Ubuntu's `fonts-dejavu-core`.

Example Linux AMD64:

```sh
chmod +x XCstream-0.9.10-beta-linux-amd64 bin/ffmpeg bin/ffprobe
./XCstream-0.9.10-beta-linux-amd64
```

macOS uses `./XCstream-0.9.10-beta-darwin-arm64` on Apple Silicon or
`./XCstream-0.9.10-beta-darwin-amd64` on Intel.
Windows uses `.\XCstream-0.9.10-beta-windows-amd64.exe` or
`.\XCstream-0.9.10-beta-windows-arm64.exe`.

These beta binaries are unsigned and not notarized. After checking provenance
and checksums, macOS may require approval in System Settings → Privacy &
Security for XCstream and its bundled tools. Windows may display SmartScreen.
Do not disable system security globally. After verifying and trusting the
package, macOS users can clear quarantine from inside the extracted XCstream
directory:

```sh
xattr -dr com.apple.quarantine .
```

Run that command only from the extracted package directory.

## Configuration and first launch

First interactive launch guides initial configuration, validates before saving,
and waits for Enter to launch. `--setup` opens the full terminal management
utility and saves/exits. Configuration defaults to XCstream.json beside the
executable. Use a writable installation/config directory. There is no browser
configuration UI.

Standard M3U and Both modes require a readable local M3U file; XMLTV is optional.
Direct-only requires neither. All integrations share one XCstream-owned tuner pool.

For service or integration use:

```sh
./XCstream-0.9.10-beta-linux-amd64 --headless --config /path/XCstream.json
```

Headless mode never prompts. SIGINT/SIGTERM request owned cleanup. Run as a
dedicated user, allow a graceful shutdown interval, and keep listeners on a
trusted network. `/dashboard` provides runtime visibility; `/kms` is the compact
embedded view. Standalone endpoints are `/playlist.m3u` and `/epg.xml`.

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

## Provenance, notices and beta limitations

The documentation/license refresh changes ZIP checksums, not the qualified
executables, media tools or frozen runtime. Use the accompanying SHA256SUMS for
these exact packages. BUILD.json retains original source revision
`c4ab9ec3eb96413b66afe4f4a2519c983ea6d1a8`, native architecture and tool hashes.

See [RELEASE.md](RELEASE.md) for completed qualification and limitations,
[KERNEL-MEDIA-SERVER.md](KERNEL-MEDIA-SERVER.md) for the Direct contract, and
`notices/` for third-party licenses and source information. Native Intel media
qualification passed; the additional Rosetta check failed as documented.
Windows interactive/service-control and downstream playback certification remain
outstanding. This beta is not production-, DVR-, or client-certified.

## Bug reports and feature requests

Use [GitHub Issues](https://github.com/Xboxilla/XCstream/issues) for bug reports,
compatibility problems, installation difficulties, recovery or recording failures,
and feature requests. Reading issues is public; creating one may require a GitHub
account. Include the XCstream version, operating system and reproduction steps.
Remove provider credentials, tokens and other private information from any logs
or screenshots before posting. Discussions are not enabled.
