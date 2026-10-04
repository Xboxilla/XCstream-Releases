# XCstream v0.9.8-beta — private binary packages

Source commit: `257fc075dc378c84ea048c3285bfabf52e3ad2c2`
Distribution tag: `v0.9.8-beta`
Build workflow: https://github.com/Xboxilla/XCstream/actions/runs/37159715033

**555 tests passed, 0 failed, 0 skipped.** Compile/protected-core/P0 checks passed.
All six native architectures built successfully and passed packaged executable
help/version, generated-config and missing-headless-config smoke checks.
Linux AMD64 source and packaged executables each passed all six SIGINT/SIGTERM
cases: idle, /watch and /direct, including repeated signals, with listeners and
owned media processes cleaned up. Source and packaged interactive setup gates
also passed, including clean Ctrl-C and the first-run launch pause in all modes.
Other-platform service-control, end-to-end playback and extended soak are not
inferred from these native CLI/configuration smoke checks.

This build includes the latest configuration cleanup, setup/shutdown polish and
conditional disk-only endpoint logging. Proxy and Dashboard are always logged;
KMS, M3U and EPG XML are logged only when their configuration is enabled. These
entries never appear in the runtime terminal, HUD or Recent Events. The first-run
setup completion screen may still show M3U/EPG URLs before Enter to launch.
No protected media/recovery behavior changed. The runtime product banner remains
v0.9.8-beta. Every ZIP's BUILD.json identifies the exact source commit above.

**No XCstream source code or source history is included in this binary repository.**
Its Git history contains distribution documents/manifests only. GitHub source
archives therefore contain only those documents, not XCstream engine source.
Python executable packaging is not encryption or a reverse-engineering barrier.

Six native ZIPs and a fresh ZIP-only SHA256SUMS are attached. Each ZIP contains
BUILD.json with the full source commit, target/native architecture and binary
hash. No Python or Docker runtime is needed. FFmpeg/ffprobe are external and
must be supplied as a qualified matching pair. Private unsigned/not notarized
beta; operating-system approval may be needed. No new license terms are added.
Linux packages use Ubuntu 22.04/glibc 2.35; macOS packages use native macOS 15
runners; Windows packages use Windows 2022/Windows 11 ARM runners.
