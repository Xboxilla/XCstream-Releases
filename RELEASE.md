# XCstream v0.9.8-beta.1 — refreshed private binary packages

Source commit: `9019bf9` (`9019bf971f2344f088606bb811e0409ff4181029`)
Source tag: `v0.9.8-beta.1`
Build workflow: https://github.com/Xboxilla/XCstream/actions/runs/37145569453

**541 tests passed, 0 failed, 0 skipped.** Compile/protected-core/P0 checks passed.
All six native architectures built successfully and passed packaged executable
help/version, generated-config and missing-headless-config smoke checks.
Linux AMD64 source and packaged executables each passed all six SIGINT/SIGTERM
cases: idle, /watch and /direct, with listeners/owned media processes cleaned up.
Other-platform service-control, end-to-end playback and extended soak are not
inferred from these native CLI/configuration smoke checks.

This build includes the audited four-setting retirement, fixed 50-event
internal retention, terminal setup colors and updated common ENV hint.
No protected media/recovery behavior changed. The runtime product banner
remains v0.9.8-beta; .1 identifies this packaging/source revision.

**No XCstream source code or source history is included in this binary repository.**
Its Git history contains distribution documents/manifests only. GitHub source
archives therefore contain only those documents, not XCstream engine source.
Python executable packaging is not encryption or a reverse-engineering barrier.

Six native ZIPs and a fresh ZIP-only SHA256SUMS are attached. Each ZIP contains
BUILD.json with the full source commit, target/native architecture and binary
hash. No Python or Docker runtime is needed. FFmpeg/ffprobe are external and
must be supplied as a qualified matching pair. Private unsigned/not notarized
beta; operating-system approval may be needed. No new license terms are added.

The previous v0.9.8-beta release remains intact for provenance.
