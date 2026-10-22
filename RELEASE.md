# XCstream v0.9.10-beta — Proprietary Beta Release

Copyright © 2026 Eyal Benedek. All rights reserved.
Use and distribution of the proprietary XCstream components are governed by
[LICENSE-XCSTREAM.md](LICENSE-XCSTREAM.md). Separately licensed dependencies
retain their applicable rights and notices.

XCstream provides live-stream continuity and MPEG-TS recovery. This package set
contains the previously qualified native executables with updated public-facing
documentation and a proprietary XCstream license. It is **documentation-only
repackaging**, not a new executable build or a new application version.

## Changes since v0.9.8-beta

- Guided Initial Setup and a full terminal Setup utility, safe local-path editors,
  validation before atomic save, Review paging, and terminal restoration.
- Functional FFmpeg/ffprobe discovery and preflight; native FFmpeg User-Agent
  unless a custom value is configured.
- Persistent validated Default and Matched Slate assets, optional Custom Slate
  video, bounded background preparation, profile matching, and fallback.
- Protection during slow initial upstream acquisition.
- Simplified Buffer presentation and attributed Slate disk diagnostics.
- Missing standalone channels fail before tuner admission; Direct duplicate
  protection, shared tuners, session ownership and cleanup remain intact.

Streaming Priority and Protected Slate Handoff are not available settings in
this version. MPEG-TS delivery, media, buffering, recovery, session ownership
and shutdown behavior are unchanged by this documentation refresh.

## Bundled dependencies and installation requirements

All six packages include native Jellyfin FFmpeg/ffprobe 7.1.3-4 portable GPL
builds, pinned by SHA-256. Python is frozen into XCstream. No separate Python
installation or Docker runtime is required. Keep the adjacent `bin` directory.
Linux also requires the included `_internal` runtime directory, glibc 2.35+
and suitable system fonts for Slate text rendering.

See `notices/FFMPEG.md`, the GPL/LGPL license texts, Python and psutil notices,
and BUILD.json for third-party provenance. Upstream FFmpeg source, patches and
build recipes: https://github.com/jellyfin/jellyfin-ffmpeg/tree/v7.1.3-4.
These notices do not license XCstream's proprietary application source.

## Original build provenance and source qualification

Source revision: `c4ab9ec3eb96413b66afe4f4a2519c983ea6d1a8`.
Original native build run identifier: `39715246053`.
Every package's BUILD.json retains that qualified source revision, original
native-build evidence, executable hashes, media-tool hashes and runtime hashes.
No private CI access is needed to inspect the supplied provenance records.

The original source qualification completed **770 passed, 0 failed, 0 skipped**.
Complete interactive Setup qualification: **14 passed**.
Source idle, `/watch`, and `/direct` shutdown: **12 passed**, covering SIGINT,
SIGTERM and repeated signals. Compile and protected-source checks passed.
Additional Linux GNU Readline and native macOS libedit cancellation checks
passed, including 40 integrated cases on each and 100 widened GNU typeahead-race
checks using the original deadlines.

These are the original qualification results, not newly run regression tests.
The Setup cancellation and first-launch prompt correction is preserved; no
streaming initialization, runtime signals, media validation or recovery changes
were made during repackaging.

## Per-platform qualification

All six builds ran on matching native CI runners. Each passed executable and
bundled-tool architecture checks, frozen CLI/config/missing-config smoke checks,
native adjacent-bin discovery and functional media preflight.

| Package | Native build and smoke | Additional qualification / limits |
|---|---|---|
| Linux AMD64 | Passed on native x86-64 Linux | Packaged 12 shutdown cases, 14 interactive Setup cases and 10 repeated cancellation cases passed. Local source checks used AMD64 Docker emulation on an ARM64 Mac. |
| Linux ARM64 | Passed on native ARM64 Linux | Packaged 12 shutdown cases, 14 interactive Setup cases and 10 repeated cancellation cases passed. |
| macOS AMD64 | Passed on native Intel macOS | Native bundled-media qualification passed. Additional Rosetta execution failed before Setup; no translated interactive pass is claimed. |
| macOS ARM64 | Passed on native Apple Silicon macOS | Downloaded executable passed 12 additional real-terminal cancellation cases on an M1 Mac, including first-run launch-pause cancellation. |
| Windows AMD64 | Passed on native Windows x64 | Native CLI/config and media preflight passed. Interactive console cancellation, Windows service/control events and downstream playback are not certified. |
| Windows ARM64 | Passed on native Windows ARM64 | Native CLI/config and media preflight passed. Interactive console cancellation, Windows service/control events and downstream playback are not certified. |

## Rosetta limitation — failed check retained

The additional Intel macOS package run through Rosetta on Apple Silicon exited
**2** before Setup with **`ffmpeg identity: timed out`**. That test **failed**;
it is not a successful cancellation or compatibility test. Native Intel CI
package/media qualification passed. Rosetta translation is not one of the six
native deployment targets. No timeout increase, validation change, workaround
or rebuild was used. Apple Silicon users should select `darwin-arm64`.

## Documentation-only repackaging and integrity

The original qualified XCstream executables, FFmpeg/ffprobe, frozen runtime,
all third-party notices and embedded BUILD.json files are unchanged byte-for-byte.
File paths and executable permission bits are preserved. README, RELEASE and
integration documentation are updated, and LICENSE-XCSTREAM.md is added.

**ZIP hashes have changed.** Verify these archives against their accompanying
SHA256SUMS, not an earlier manifest. The manifest covers the six ZIPs, combined
BUILD.json, README.md, RELEASE.md, KERNEL-MEDIA-SERVER.md and LICENSE-XCSTREAM.md.
BUILD.json is unchanged because it records native payload hashes and build
provenance rather than ZIP archive hashes. No new build or certification is implied.

## Remaining beta limitations

- No prolonged production soak, actual downstream DVR/player certification or
  hardware-specific decode/encode certification is claimed.
- Custom Slate/profile fallback should receive real client playback testing.
- Windows interactive console cancellation and service-control behavior remain
  outside the completed qualification.
- Source formats, hardware and downstream clients can affect recovery results.
- Binaries are unsigned and not notarized; see README.md for launch guidance.

The beta is provided for evaluation and field testing, not as production-certified
software. Older releases remain available as historical provenance.
