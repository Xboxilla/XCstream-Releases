# XCstream v0.9.10-beta

Private beta. One application and one immutable local-source snapshot for six
native targets. BUILD.json records that commit and the dependency provenance.

## Changes since the distributed v0.9.8-beta

- Expanded terminal Initial Setup and full Setup utility, safe local-path editors,
  validation before atomic save, Review paging and terminal-state restoration.
- Functional FFmpeg/ffprobe discovery/preflight; native FFmpeg User-Agent unless
  an explicit custom value is configured.
- Persistent validated Default/Match Slate assets and optional Custom Slate video,
  bounded background preparation, profile matching and validated fallback.
- Preserved first-secure-upstream protection for slow initial acquisition.
- Simplified Buffer presentation and refined attributed Slate disk diagnostics.
- Missing standalone channels fail before tuner admission; Direct ownership,
  duplicate protection and shared-tuner semantics remain intact.

Streaming Priority and Protected Slate Handoff are not available settings in this
version. This release does not restore those removed options or a second media
engine. Existing media, recovery, session and shutdown behavior is unchanged by
the packaging work.

## Bundled dependencies

All six packages include Jellyfin FFmpeg/ffprobe 7.1.3-4 portable GPL builds,
selected by native target and pinned SHA-256. Python is frozen into XCstream.
There is no Docker runtime requirement. Keep the adjacent bin directory.
Linux additionally includes a required `_internal` frozen runtime directory. Its
single-process folder packaging preserves the application's signal handling without
a onefile parent forwarding a terminal Ctrl-C a second time. Application code is
unchanged; the strict cancellation and service-shutdown tests remain mandatory.
Linux requires glibc 2.35+ and system fonts for existing Slate text rendering.
See notices/FFMPEG.md and BUILD.json for publisher, source, licenses and hashes.

## Verification and limitations

Each published package must pass executable architecture checks, frozen help,
config-generation and missing-config failure checks, module-presence checks, and
native bundled-pair functional media preflight. The release-level verification
matrix supplied with the published assets records actual completed checks.
Linux package qualification additionally exercises idle, /watch and /direct
SIGINT/SIGTERM, repeated signals and terminal setup.

Windows packages without native runtime smoke evidence are **EXPERIMENTAL — not
natively smoke-tested**. Do not interpret a successful build as playback or
service certification. macOS Intel checks performed through Rosetta are translated,
not Intel-hardware tests. Container/emulation checks are identified as such.

No prolonged production soak, actual downstream DVR/player certification, or
hardware-specific decode/encode certification is claimed. Custom Slate/profile
fallback should receive real Kernel Media Server/client playback testing.
The binaries are unsigned and not notarized. Beta field-testing feedback is welcome.

No proprietary XCstream source or source history belongs in XCstream-Releases.
Older releases remain available for provenance.

## Qualification of this published package set

Source commit: `c4ab9ec3eb96413b66afe4f4a2519c983ea6d1a8`.
Native build run: `39715246053`. Every package's BUILD.json identifies this same
clean source revision. These are the existing qualified packages; no source or
media-tool validation changes were made for release assembly.

The Setup cancellation correction keeps interactive POSIX editing off the main
signal-handling thread. The first-run `Press Enter to launch XCstream...` pause
uses that same corrected reader, preserving its exact text, Enter behavior,
injected readers, exit 130, and terminal restoration. Streaming initialization,
runtime signal handling, media validation, and recovery were not changed.

Source qualification: **770 passed, 0 failed, 0 skipped**. Full real-terminal
Setup qualification: **14 passed**. Source idle/watch/direct shutdown:
**12 passed**, covering SIGINT/SIGTERM and repeated signals. Compile and
protected-source checks passed. Additional source cancellation checks passed on
Linux GNU Readline and native macOS libedit, including 40 integrated cases on
each and 100 widened GNU typeahead-race checks with the original deadlines.

### Per-platform verification matrix

All six builds ran on matching native GitHub runners. Each passed executable and
bundled-tool architecture checks, frozen CLI/config/missing-config smoke checks,
and native automatic discovery plus the application's functional media preflight.

| Package | Native build and smoke | Additional qualification / limits |
| --- | --- | --- |
| Linux AMD64 | Passed on native x86-64 Linux | Packaged 12 shutdown cases, 14 interactive Setup cases, and 10 repeated cancellation cases passed. Local source checks used AMD64 Docker emulation on an ARM64 Mac. |
| Linux ARM64 | Passed on native ARM64 Linux | Packaged 12 shutdown cases, 14 interactive Setup cases, and 10 repeated cancellation cases passed. |
| macOS AMD64 | Passed on native Intel macOS | Native bundled-media qualification passed. Additional Rosetta execution failed before Setup; see the explicit limitation below. No translated interactive pass is claimed. |
| macOS ARM64 | Passed on native Apple Silicon macOS | Downloaded executable passed 12 additional real-terminal cancellation cases on an M1 Mac, including first-run launch-pause cancellation. |
| Windows AMD64 | Passed on native Windows x64 | Native CLI/config and media preflight passed. Interactive console cancellation, Windows service/control events and downstream playback are not certified. |
| Windows ARM64 | Passed on native Windows ARM64 | Native CLI/config and media preflight passed. Interactive console cancellation, Windows service/control events and downstream playback are not certified. |

### Rosetta limitation — failed check retained

The additional Intel macOS package run through Rosetta on an Apple Silicon Mac
exited **2** before reaching Setup: **`ffmpeg identity: timed out`**. That check
**failed** and is not presented as a successful cancellation or compatibility test.
The native Intel CI package/media qualification passed. Rosetta translation is
not one of the six native deployment targets; the owner explicitly accepted this
as a documented beta limitation. No timeout increase, validation change, retry
workaround, or rebuild was used. Apple Silicon users should select darwin-arm64.

The six ZIPs retain their native build bytes. Release assembly verifies their
exact source commit, executable/tool architectures and hashes, frozen runtime
contents, required documentation/notices and source-free file allowlists.
SHA256SUMS covers all six ZIPs, the combined BUILD.json and release documents.
This beta is not a production soak, actual DVR/player, or hardware certification.
