# Party Chat update repository

The official public release and update manifest for Party Chat.

## Current release: 1.0.2

- `PartyChat.html` — complete self-contained app.
- `manifest.json` — current version and SHA-256 checksum.
- `changelog.txt` — release notes.

## Update endpoints

- Manifest: https://raw.githubusercontent.com/ekemp20-del/party-chat-updates/main/manifest.json
- App: https://raw.githubusercontent.com/ekemp20-del/party-chat-updates/main/PartyChat.html

GitHub only distributes application updates. Chat messages, presence and images continue to use the existing Party Chat WebSocket relay.

## How client updates work

Party Chat checks the public manifest at startup and periodically while open. It downloads a newer HTML build, checks its version marker and SHA-256 checksum, and stages the verified build in browser storage. Users restart Party Chat to apply it, so an active conversation is not interrupted.

A browser HTML file cannot overwrite its own original local file in the normal sandbox. The updated build is therefore launched from browser storage on subsequent launches. Users should continue opening the same original HTML file. If browser storage is unavailable or disabled, the local version remains available and the app continues to run.

## Publishing a new release

1. Replace `PartyChat.html` with the full new app build.
2. Update the version marker in the document, update bootstrap, and updater code.
3. Recalculate the SHA-256 checksum of the exact UTF-8 `PartyChat.html` file and update `manifest.json`.
4. Update `changelog.txt` and commit the HTML first, then the manifest.
