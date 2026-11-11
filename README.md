# Party Chat update repository

This public repository hosts the official Party Chat HTML releases and update manifest. GitHub is used only to distribute application updates; chat messages, images, presence and other live traffic continue to use the existing Party Chat WebSocket relay.

## Release files

- `PartyChat.html` — complete self-contained application.
- `manifest.json` — current version, release filename and SHA-256 checksum.
- `changelog.txt` — human-readable release notes.

## Update endpoints

The app reads these public raw-file URLs:

- https://raw.githubusercontent.com/ekemp20-del/party-chat-updates/main/manifest.json
- https://raw.githubusercontent.com/ekemp20-del/party-chat-updates/main/PartyChat.html

No GitHub account or token is required on users' devices.

## How updates work

Party Chat checks the manifest at startup and periodically while open. When a newer version is available, it downloads the HTML, validates the version marker and SHA-256 checksum, then stages the verified HTML in browser storage. Users restart Party Chat to activate it, avoiding interruption to active conversations.

Because a normal local HTML file cannot overwrite itself, the local file acts as a bootstrap. The verified newer HTML is loaded from browser storage on the next launch. Browser settings that disable local storage may prevent staged updates from being applied.

## Publishing a release

1. Replace `PartyChat.html` with the complete new application build.
2. Update `manifest.json` with the new version and the SHA-256 checksum of the exact UTF-8 file bytes.
3. Commit both files to the `main` branch. Update `changelog.txt` with the release notes.

Keep the repository public so clients can fetch updates without credentials.
