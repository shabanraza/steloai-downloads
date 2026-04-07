# steloai-downloads
Public desktop installers and updater assets for SteloAI

## Automated macOS notarization

This repository includes a GitHub Actions workflow at `.github/workflows/notarize-macos-release.yml` that:

- triggers on every published release (or manual dispatch),
- downloads all `.dmg` assets from that release,
- extracts the `.app`, re-signs it with Developer ID,
- rebuilds the DMG, notarizes it, staples the ticket,
- uploads the notarized DMGs back to the same release (`--clobber`).

### Required GitHub repository secrets

- `APPLE_ID`
- `APPLE_APP_SPECIFIC_PASSWORD`
- `APPLE_TEAM_ID`
- `APPLE_CERT_P12_BASE64` (base64 of your signing cert `.p12`)
- `APPLE_CERT_PASSWORD`
- `APPLE_DEVELOPER_ID_APPLICATION` (example: `Developer ID Application: Your Name (TEAMID)`)
- `KEYCHAIN_PASSWORD` (temporary keychain password for CI)

### Manual run

Go to **Actions → Notarize macOS release assets → Run workflow** and optionally provide a `tag`.
