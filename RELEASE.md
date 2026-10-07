# XCstream v0.9.9-beta — private native binaries

Source commit: `eed993ed0385de63c9b381a64ebde64a717c734b`
Source branch: `development/v0.9.9-beta`
Source/distribution tag: `v0.9.9-beta`
Build/qualification: https://github.com/Xboxilla/XCstream/actions/runs/37553673980

## Changes

- Setup adds DVR/Live TV priority presets over six existing settings, derived
  Custom recognition, Default/Automatic terminology and 19 Advanced controls.
  DVR remains the default with a 128 KB serving gate; Live TV uses the same
  engine with the specified faster settings and a 64 KB gate.
- Matched synthetic Slate is generated asynchronously, validated by probe and
  decoder, and reused by normalized media contract for the process lifetime.
  Builds are deduplicated and bounded. Generic H.264/HEVC Slate stays available
  as fallback. Dynamic assets are fenced and cleaned at process shutdown.
- Protected Slate Handoff is optional and Disabled by default. Enabled sessions
  keep Slate public while private recovery proves sustained byte/clock and
  independent processing progress, an exact compatible profile and an in-band
  configuration/IDR start. The same qualified process transfers through existing
  recovery tickets and the existing bounded publication queue/timeline.

Provider video remains stream-copy. No HLS/DASH packaging, provider transcoding,
second tuner pool or observer recovery authority is added. The private v0.9.8
source baseline and released artifacts remain unchanged.

## Qualification

643 full-suite tests passed, 0 failed, 0 skipped; compile and protected-core/P0
checks passed. Linux source and packaged service qualification cover idle,
/watch and /direct with SIGINT/SIGTERM, plus repeated signals: six ordinary and
six repeated cases each. Fourteen real-PTY Setup cases cover first-run modes,
explicit setup, save/quit, invalid configuration and plain/partial-input Ctrl-C.

Real matched-Slate encode/probe/decode qualified H.264 + AC3 5.1, HEVC + AAC,
and 10-bit HEVC + EAC3 5.1. Protected H.264 and HEVC gates exercise repeated
outage/return cycles; HEVC includes reordered pictures and writer failure.
The disabled legacy-return gate also passes. Raw captures retain exact
ring-to-HTTP byte identity, elementary-packet identity and timestamp/PCR checks.
Finite-file decoding uses a separate completed-PES snapshot, excluding only
open final units at the arbitrary live capture cutoff. Earlier corruption
remains a failure, verified by a real-decoder negative test.

All six native targets passed architecture verification, 57 native
Setup/cache/handoff tests and frozen executable help/configuration smoke
checks before publication. BUILD.json records the exact source and build run.
Linux AMD64 additionally runs the packaged service and real-PTY Setup gates.
Other-platform service control, end-to-end player behavior and extended
production soak are not implied by native CLI/configuration smoke checks.

## Distribution and limitations

Six raw native executables and six optional ZIPs are provided with BUILD.json,
SHA256SUMS and notices/documentation. No Python/Docker runtime is required.
FFmpeg/ffprobe are external and must be supplied as a qualified matching pair.
No XCstream source files, test sources or private Git history are included.
Python executable packaging is not encryption or a reverse-engineering barrier.

Protected handoff conservatively retains Slate for mismatched profiles, sources
starting with inter-coded pictures/HEVC CRA instead of a configured IDR, or
private attempts exceeding the bounded 16 MB prefix. Unsupported matched-Slate
profiles use the fixed fallback. Legacy return remains available with Protected
Handoff Disabled. These beta constraints are intentional abstention, not proof
that every downstream decoder or source profile is qualified.

Linux builds use Ubuntu 22.04/glibc 2.35; macOS uses native macOS 15 runners;
Windows uses Windows 2022/Windows 11 ARM runners. Unsigned/not notarized private
beta; verify checksums before OS approval. No new licensing terms are added.
