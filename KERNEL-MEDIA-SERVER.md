# Kernel Media Server integration — XCstream v0.9.10-beta

Enable `kms_direct_enabled` in XCstream.json (or XC_KMS_DIRECT_ENABLED).
Launch with `--headless --config /path/XCstream.json`. M3U is optional in Direct
mode; configured `/watch` channels and Direct use the same XCstream-owned tuners.

`GET /direct` opens one long-lived MPEG-TS response.

Request headers:

- `XCstream-Source`: required upstream HTTP/HTTPS stream URI.
- `XCstream-Name`: optional safe display name; otherwise Kernel Media Server Direct.
- `XCstream-Proxy`: optional per-session HTTP/HTTPS/SOCKS5 proxy URI.
- `XCstream-XMLTV-ID`: optional stable XMLTV channel identity.

Do not put credentials in display names. Source/proxy secrets are not operator
identities. XMLTV metadata can advance while the session retains its channel
identity. Proxy/source ownership survives the same session's recovery.

Responses advertise `XCstream-Tuner-Capacity`:

| Status | Meaning |
|---|---|
| 200, Content-Type: video/mp2t | Continuous MPEG-TS body |
| 400 | Invalid/missing Direct source or malformed metadata |
| 404 | Direct integration disabled |
| 409, XCstream-Reason: source-active | Same source is already owned; original stream is untouched |
| 503, XCstream-Reason: tuner-releasing, Retry-After: 2 | Owned final cleanup; retry after two seconds, not a release guarantee |
| 503, XCstream-Reason: tuner-capacity | Genuine concurrent exhaustion; no Retry-After |

Other setup/shutdown/overload failures retain their HTTP error semantics.
HEAD /direct never admits a tuner (405 when enabled, 404 when disabled).
A missing `/watch/<channel>` also returns 404, but means an unknown standalone
lineup channel, not disabled Direct integration.

Kernel closes the HTTP body when its session ends. XCstream alone owns admission,
Watchdog/Validator, recovery, Slate, generation fencing and final tuner reuse.
Never force-release or reset a tuner. A recovery/Slate episode still owns the source.

Use `--kms-origin` with the exact scheme/host/port permitted to frame `/kms`.
The ordinary dashboard remains non-frameable. This is a trusted-network interface,
not a public authenticated ingest endpoint. No HLS/DASH or DVR API is added.
