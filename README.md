# XCstream binary releases

This **private** repository contains native XCstream binary release downloads
and documentation only. It contains no XCstream source files or source history.
Download v0.9.8-beta from this repository's Releases page and verify SHA256SUMS.
GitHub's automatically generated source archives contain these documents only,
not the XCstream engine. No license grant or redistribution permission is added.

XCstream is one standalone MPEG-TS continuity engine with optional Kernel Media
Server Direct integration. XCstream owns all virtual tuners and recovery.

Unzip the package for your OS/CPU. For Linux AMD64, for example:

```sh
chmod +x XCstream-0.9.8-beta-linux-amd64
./XCstream-0.9.8-beta-linux-amd64 --setup
./XCstream-0.9.8-beta-linux-amd64 --headless --config /path/to/XCstream.json \
  --ffmpeg-path /path/to/ffmpeg --ffprobe-path /path/to/ffprobe
```

No Python or Docker runtime. FFmpeg/ffprobe are external matching qualified
tools; absent overrides, XCstream expects installation-relative bin/ffmpeg and
bin/ffprobe (.exe on Windows), not PATH. Default configuration is XCstream.json
beside the executable. Use writable log/buffer/cache locations.

macOS packages are not Developer ID signed/notarized. Approve this trusted
private download using macOS Privacy & Security if Gatekeeper blocks it.
Windows may likewise require unsigned-application approval.

The source build commit `d24d8e18cdc673495bab69f0c7d53724143c10d6` is recorded for traceability only; binary
repository access does not grant access to the private source repository.
Python executable packaging is not encryption or a reverse-engineering barrier.
