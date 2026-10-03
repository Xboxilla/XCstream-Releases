# XCstream v0.9.8-beta — private binary beta

Six native packages copied byte-for-byte from one authoritative source build.
Source build commit: `d24d8e18cdc673495bab69f0c7d53724143c10d6`. Source release tag: `v0.9.8-beta`.
Verify SHA256SUMS before running. Each ZIP contains BUILD.json provenance.

No Python or Docker runtime is required. FFmpeg and ffprobe are not included;
supply the qualified matching pair using --ffmpeg-path and --ffprobe-path.
See README.md and KERNEL-MEDIA-SERVER.md for launch/integration instructions.

Native executable/config smoke passed on all six platforms. Linux AMD64 also
passed idle, /watch and /direct SIGINT/SIGTERM gates. Extended soak and full
media/service-control qualification on other platforms remain outstanding.
Unsigned/not notarized private beta; normal operating-system approval may be
required. Source cleanup commits after the above tag are not in these packages.
