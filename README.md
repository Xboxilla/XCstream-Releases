# XCstream private binary releases

Current refreshed release: [v0.9.8-beta.1](https://github.com/Xboxilla/XCstream-Releases/releases/tag/v0.9.8-beta.1).
Source commit: `9019bf9` (`9019bf971f2344f088606bb811e0409ff4181029`). 541 tests passed, 0 failed, 0 skipped.
This repository contains native binary releases and distribution documentation
only: no XCstream source files or source history. Binary repository access does
not grant access to the separate private source repository.

Choose the ZIP matching your OS/CPU and verify SHA256SUMS. Six targets:
Linux AMD64/ARM64, macOS AMD64/ARM64 and Windows AMD64/ARM64.
Each archive carries BUILD.json provenance and third-party notices.

No Python/Docker runtime required. FFmpeg and ffprobe are not included.
Supply the qualified matching tools; default paths are bin/ffmpeg and
bin/ffprobe beside the executable (.exe on Windows), not PATH.

Linux AMD64 launch example (the product filename/version remains v0.9.8-beta):

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

Old v0.9.8-beta packages remain available unchanged for provenance.
No license or redistribution grant is added. Python executable packaging is not
encryption or protection from reverse engineering.
