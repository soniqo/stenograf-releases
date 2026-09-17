# Stenograf releases

Official installers and release notes for [Stenograf](https://soniqo.audio/stenograf), a local-first meeting transcription app.

[Browse releases](https://github.com/soniqo/stenograf-releases/releases) · [Help](https://soniqo.audio/stenograf/help) · [System requirements](https://soniqo.audio/stenograf/requirements)

## Install on a Mac

1. Choose an Apple Silicon DMG from a release. Check its notes and known limitations; a prerelease is a testing build.
2. Open the DMG and drag Stenograf into Applications, replacing your previous app if you are updating.
3. Launch Stenograf from Applications and follow the sign-in and setup screens.

The macOS installer requires Apple Silicon and macOS 15 or later. Local language-model features require at least 16 GB of memory. Installers are signed with Developer ID and notarized by Apple.

Each release includes `SHA256SUMS.txt`. To verify a downloaded installer, place it beside that file and run `shasum -a 256 -c SHA256SUMS.txt` in that folder.

Replacing the app is separate from its local recordings. If the app reports a database version mismatch, install a compatible newer build; do not delete the database to bypass it.

## Report a problem

For a transcription failure, choose **Report a problem** in the app, review the details and send the report to support. You can also contact **info@soniqo.audio**. Avoid posting private meeting content in public GitHub issues.

## About this repository

This repository distributes installers and release notes. It does not contain Stenograf's application source code or grant an open-source license to the app. Use is governed by the [Stenograf terms](https://soniqo.audio/stenograf/terms) and [privacy policy](https://soniqo.audio/stenograf/privacy).

Publishing an installer here does not automatically announce it to existing installations. Recommended-version notices are managed separately.
