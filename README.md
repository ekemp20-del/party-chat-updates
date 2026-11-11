# Party Chat

Official public release repository and update feed for Party Chat.

## Current release: 1.0.3

- `PartyChat.html` — complete self-contained application.
- `manifest.json` — current version and SHA-256 checksum.
- `changelog.txt` — release notes and repair information.

## Update endpoints

- Manifest: https://raw.githubusercontent.com/ekemp20-del/party-chat-updates/main/manifest.json
- App: https://raw.githubusercontent.com/ekemp20-del/party-chat-updates/main/PartyChat.html

GitHub distributes the app only. Chat messages, presence and images continue to use the existing Party Chat WebSocket relay.

## Important: one-time repair from v1.0.2

Party Chat v1.0.2 used `document.write()` in an early `<head>` script to activate a cached update. Some browsers resumed parsing the original HTML after the update had been written, which could show two copies of the interface. Replace your local `PartyChat.html` file with v1.0.3 once to repair this. The v1.0.2 updater cannot safely replace its own faulty bootstrap.

## How updates work from v1.0.3 onward

Party Chat checks the public manifest at startup and periodically while open. A newer HTML release is downloaded, checked for its version marker and verified using SHA-256, then staged in browser storage. Users restart Party Chat to apply it without interrupting an active conversation.

The updated HTML is loaded in one full-screen `srcdoc` frame that inherits the local file's origin. The original downloaded file remains the launch point, so the staged release is retained in browser storage between launches. Restarting from a staged release returns to the original local file, where the newest staged version is activated. The app continues to run normally if no update is available; if browser storage is disabled, staged updating may not be available.

## Publishing a release

1. Create the complete standalone HTML build and update all embedded version markers.
2. Calculate the SHA-256 checksum of the exact UTF-8 HTML bytes.
3. Update `manifest.json` with the new version, filename and checksum.
4. Update `changelog.txt` and commit the HTML first, then the manifest.
