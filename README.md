# Party Chat — v1.0.4

Official public app release and update manifest.

## Update hosting

- Manifest: https://raw.githubusercontent.com/ekemp20-del/party-chat-updates/main/manifest.json
- App: https://raw.githubusercontent.com/ekemp20-del/party-chat-updates/main/PartyChat.html

GitHub is used only to distribute application files. Chat messages, presence and images continue to use the existing Party Chat WebSocket relay.

## Manual update flow

No update check or download runs at startup or in the background. Users open Settings and select Check for updates. If a newer verified release exists, they can:

- Download new HTML — save a replacement standalone HTML file and replace their existing launch file manually.
- Patch this browser — save the new HTML in browser storage and run it through the existing local launch file. The original file on disk is not overwritten because normal browser HTML cannot write to its own local file.

Before patching, Party Chat saves the currently running HTML as a previous-version backup. Settings then offers a Rollback button. Rollback uses the saved backup and can force the browser to run it even if the local launch file has a different version.

## Migration from earlier versions

The v1.0.4 bootstrap removes only the obsolete staging key from previous automatic updaters. Existing display name, theme, dark mode, message history and other user data are deliberately kept. Users should replace their existing PartyChat.html with v1.0.4 once, overwriting it in the same folder with the same filename. Keeping the same file path is important because browser storage for a local HTML app can be associated with that file location; saving it as a different filename may make the old name, theme and history appear to be missing. This one-time replacement installs the new manual update interface and migration logic.

## Publishing a release

1. Update all app and bootstrap version markers in PartyChat.html.
2. Calculate SHA-256 over the exact UTF-8 bytes of the final HTML file.
3. Update manifest.json with the version, file name and checksum.
4. Update changelog.txt and publish the HTML before publishing the manifest.
