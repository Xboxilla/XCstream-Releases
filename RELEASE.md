# XCstream v0.9.8-beta — private binary packages

Source commit: `105d87202fa3b4243bb917c9b98348d5dc189d1c`
Distribution tag: `v0.9.8-beta`
Linux/macOS build workflow: https://github.com/Xboxilla/XCstream/actions/runs/37267930856
Windows build workflow: https://github.com/Xboxilla/XCstream/actions/runs/37337427786

**600 tests passed, 0 failed, 0 skipped.** Compile/protected-core/P0 checks passed.
All six native architectures built successfully and passed packaged executable
help/version, generated-config and missing-headless-config smoke checks.
Each native runner also passed 25 portable setup/presentation tests, checked
that the new setup modules were embedded, and verified frozen refresh defaults.
Linux AMD64 source and packaged executables each passed six ordinary plus six
repeated SIGINT/SIGTERM cases: idle, /watch and /direct. Listeners and owned media
processes were cleaned up; exit statuses were 130/143. Each also passed twelve
real-PTY setup cases: three cancellations, review/validate/save-and-exit,
edit/quit, invalid-save rejection, missing/invalid/mismatched media-tool paths,
and first-run Standard M3U, Direct and Both. Review Space/Enter paging and Q
return were exercised in a real 24-row terminal before validation/save.
Interactive Windows/macOS setup is not separately end-to-end qualified.
Other-platform service-control, end-to-end playback and extended soak are not
inferred from these native CLI/configuration smoke checks.

This build completes the terminal setup management utility and short automatic
first-run flow. It adds a compact title box, aligned values, grouped Review,
Unicode/ASCII fallback and Back navigation without a browser or full-screen TUI.
Review paging detects interactive terminal height without splitting sections;
fitting Reviews and piped output do not pause. FFmpeg/ffprobe prompts qualify
paths locally and retain automatic sibling discovery. Dashboard uptime uses
the existing arrow presentation; the embedded view remains free of uptime.
Tuners groups capacity and HDHomeRun compatibility. Matching media tools and
configuration are qualified before atomic save. M3U/XMLTV remain local-file-only;
Direct-only quick setup asks for neither. Newly created first-run configurations
start with verbose diagnostics off; existing settings, automatic advertised
host and disk-buffer defaults are retained.

HUD/Web refresh is 1–5 seconds (default 1). HUD event rows are 4–50 (default 10);
Web rows are 10–100 (default 20). Dashboard and embedded view share Web settings.
Advanced contains low-level timing, probing and maintenance controls. Terminal
Lineup/RAM label spacing and dynamic disk-only startup banner width are retained.
Conditional disk-only endpoint discovery remains absent from runtime terminal,
HUD and Recent Events; first-run setup still shows applicable URLs before launch.
No protected media/recovery behavior changed. The runtime product banner remains
v0.9.8-beta. Every ZIP's BUILD.json identifies the exact source commit above.
The build workflow provisions the existing default buffer directory only on
disposable Linux runners for qualification. It then builds a clean checkout of
the frozen source SHA; no product source or configuration default was changed.
Windows qualification compares the resolved temporary missing-file path, matching
setup's existing path resolution rather than assuming its short-path spelling is
unchanged. All 25 tests run; no test is skipped. This build-only adaptation
does not modify any file in the frozen checkout or packaged application.

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
