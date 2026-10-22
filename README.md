# PINESSHREMO

WiFi Pineapple SSH controller for phone and desktop. Connect over SSH to a Mark VII (or earlier OpenWrt Pineapple), run payloads, schedule jobs, watch live PineAP / clients / surveys, and optionally ask an AI key you bring yourself to explain or fix a failed command.

## Run (desktop)

```bash
bun install
bun run dev          # http://127.0.0.1:3000  (loopback only)
bun run lint         # tsc --noEmit
bun run build
```

Optional `.env` (see `.env.example`): `GEMINI_API_KEY` for the legacy generate/analyze endpoints. The in-app AI Fix uses a key you paste in Config (OpenAI / Anthropic / Gemini) and never sends it to this server from the phone.

## Android

```bash
bun run build
npx cap sync android
cd android && ./gradlew assembleDebug
```

The APK talks to the Pineapple directly over SSH via the bundled `PineappleSsh` Capacitor plugin — no desktop server required on the phone.

## Notes

- SSH host keys are pinned locally after the first successful connect. Forget the pin in Config if you replaced the device.
- Passwords are not persisted across reloads; enter them in Config each session.
- The Node SSH API binds to `127.0.0.1` by default. Do not set `HOST=0.0.0.0` on a shared network.
