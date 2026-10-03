# XCstream v0.9.8-beta — private binary releases

Current release: [XCstream v0.9.8-beta](https://github.com/Xboxilla/XCstream-Releases/releases/tag/v0.9.8-beta).
Source commit: `257fc075dc378c84ea048c3285bfabf52e3ad2c2`.
555 tests passed, 0 failed, 0 skipped. See RELEASE.md and BUILD-MANIFEST.json.
This repository contains native binary releases and distribution documentation
only: no XCstream source files or source history. Binary repository access does
not grant access to the separate private source repository.

Choose the ZIP matching your OS/CPU and verify SHA256SUMS. Six targets:
Linux AMD64/ARM64, macOS AMD64/ARM64 and Windows AMD64/ARM64.
Each archive carries BUILD.json provenance and third-party notices.

No Python/Docker runtime required. FFmpeg and ffprobe are not included.
Supply the qualified matching tools; default paths are bin/ffmpeg and
bin/ffprobe beside the executable (.exe on Windows), not PATH.

Linux AMD64 launch example:

```sh
chmod +x XCstream-0.9.8-beta-linux-amd64
./XCstream-0.9.8-beta-linux-amd64 --setup
./XCstream-0.9.8-beta-linux-amd64 --headless --config /path/to/XCstream.json \
  --ffmpeg-path /path/to/ffmpeg --ffprobe-path /path/to/ffprobe
```

Default JSON is XCstream.json beside the executable. Use writable log/buffer/
cache locations and trusted-network listeners. Kernel Media Server Direct and
standalone M3U share XCstream's normal tuner pool. See KERNEL-MEDIA-SERVER.md.
macOS is not Developer ID signed/notarized; trusted private downloads may need
Privacy & Security approval. Windows may likewise warn about unsigned apps.

First interactive launch without valid JSON enters terminal setup, saves
atomically, then waits for Enter before starting. Standard M3U/Both setup shows
media-server URLs before that pause; Direct-only setup does not. Explicit
--setup edits, saves and exits. Headless launch never prompts. Setup Ctrl-C
cancels cleanly with exit 130. Runtime SIGINT/SIGTERM use owned cleanup and exit
130/143, including harmless repeated signals. Startup endpoint discovery is
disk-log-only, never runtime terminal/HUD/Recent Events output.

No license or redistribution grant is added. Python executable packaging is not
encryption or protection from reverse engineering.
