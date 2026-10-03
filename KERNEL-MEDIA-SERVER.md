# Kernel Media Server Direct beta contract

Enable kms_direct_enabled in XCstream.json. KMS and /watch share XCstream's
normal tuner pool; Kernel Media Server never owns or force-releases tuners.

GET /direct (long-lived MPEG-TS response)

Request headers:
- XCstream-Source: required upstream media URI
- XCstream-Name: optional safe display name
- XCstream-Proxy: optional per-session proxy URI
- XCstream-XMLTV-ID: optional stable XMLTV identity

Responses advertise XCstream-Tuner-Capacity.
- 200, Content-Type: video/mp2t, continuous body
- 409, XCstream-Reason: source-active (same source already owned)
- 503, XCstream-Reason: tuner-releasing, Retry-After: 2
- 503, XCstream-Reason: tuner-capacity (no Retry-After)

Other failures are not tuner-capacity conflicts. HEAD /direct never tunes.
Kernel Media Server closes the HTTP stream when its session ends; XCstream
performs normal owned teardown. Retry-After is pacing, not a release guarantee.
Keep listeners on a trusted network and never log source/proxy credentials.

/dashboard is standalone runtime visibility; /kms is the compact embedded view.
Pass --kms-origin with the exact Kernel Media Server origin for /kms framing.
Configuration is terminal/JSON/ENV/CLI only, not web Options.
