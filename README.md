# T3 Chat Desktop

A Tauri-based desktop wrapper for [t3.chat](https://t3.chat).

## Features

- Native macOS desktop app
- Apple Silicon optimized
- Full t3.chat functionality

## Development

### Prerequisites

- [Node.js](https://nodejs.org/) (v20 or later)
- [Rust](https://rustup.rs/)
- Xcode Command Line Tools (macOS)

### Setup

```bash
# Install dependencies
npm install

# Run in development mode
npm run tauri dev

# Build for production
npm run tauri build
```

## Releases

This project uses GitHub Actions to automatically build and release macOS binaries when you push a new tag.

### Creating a Release

1. Update the version in `src-tauri/tauri.conf.json`
2. Commit your changes
3. Create and push a tag:
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```

The GitHub Action will automatically:
- Build the app for Apple Silicon (aarch64)
- Create a GitHub release
- Upload both DMG and App Bundle files

### Code Signing (Optional)

For distribution outside the App Store, you can set up code signing:

1. Generate a certificate in Apple Developer Console
2. Export as `.p12` file
3. Convert to base64 and add to GitHub Secrets:
   - `TAURI_SIGNING_PRIVATE_KEY`: Base64 encoded .p12 file
   - `TAURI_SIGNING_PRIVATE_KEY_PASSWORD`: Password for the .p12 file
