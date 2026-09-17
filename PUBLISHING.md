# Publishing an installer

This repository is the public artifact destination. The application source and signing configuration remain in their existing private repository.

## Current preview process

1. Merge and test the intended changes. Build a clean main checkout and record its complete commit ID.
2. Package the app for the selected platform. For the current Apple Silicon build, include the required Swift compatibility runtime in `Contents/Frameworks`, sign that library with the app's Developer ID, then sign and verify the complete bundle. Do not rely on libraries found only inside a developer's Xcode installation.
3. Check the actual packaged configuration. A service without its required app credentials must be called out as unavailable in the release notes.
4. Sign the DMG, submit it to Apple notarization, staple the accepted ticket, validate the ticket and check Gatekeeper acceptance.
5. Compute SHA-256 **after stapling**. Prepare `SHA256SUMS.txt` and `build-info.json` identifying the source commit, platform, architecture and artifact checksum.
6. Create a draft prerelease here, upload the DMG and manifests, and verify all assets before publishing. Test the public link without a signed-in GitHub session.
7. Keep prereleases separate from the recommended app version. The Console download destination and server-recommended version are separate rollout decisions.

## Stable releases

A stable release needs a new marketing version, release notes, supported-platform artifacts and the corresponding server build admission. App update notices compare the marketing version: changing only `+build-metadata` does not prompt an update.

The existing private release workflow signs artifacts but stores them in its private repository. A future automated publication step should upload only reviewed installers and manifests to this repository using a credential scoped to this destination. GitHub-hosted jobs in the private application repository are currently blocked by account billing; restore that capacity or use a controlled signing runner before relying on fully automatic releases.

Keep signing credentials and provider secrets in the private build environment. Only installers, checksums, non-secret build metadata and release notes belong in this repository.

## Recovering an interrupted upload

The public repository's **Assemble verified installer** workflow can reconstruct an installer from small draft-release assets named `<installer>.part-000`, `<installer>.part-001`, and so on. Supply the draft tag, installer filename, expected part count and SHA-256 of the complete notarized installer. It waits for the parts, concatenates them in filename order, verifies the full checksum, uploads one normal DMG, and removes the temporary parts. It leaves publication to the operator. This public artifact job runs separately from the private signing/build workflow.
