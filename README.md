# Pars Messenger iOS

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL%203.0-blue.svg)](LICENSE)

> Private messaging for the Pars Network - Built on [pars.network](https://pars.network)

## Overview

Pars Messenger iOS is a privacy-focused messaging app for the Pars Network, featuring end-to-end encryption with post-quantum cryptography. Messages are stored on decentralized storage nodes and routed through onion routing for maximum privacy.

## Current Status

**Integration Status: In Progress**

The iOS app uses `libsession-util` for networking. Full Pars Network integration requires modifications to the underlying C++ library.

### What Works
- Building and running the app
- Core messaging functionality

### What Needs Work
- Network configuration for Pars SessionVM
- libsession-util modifications
- Pars branding updates

## Installation

### Option 1: Build from Source (Recommended)

**Prerequisites:**
- Mac with Xcode 16.2+
- Apple Developer account (free tier works)
- iOS 15.0+ device

**Steps:**
```bash
git clone https://github.com/parsdao/pars-ios
cd pars-ios
open Session.xcodeproj
```

In Xcode:
1. Change Team in all TARGETS to your Apple Developer account
2. Connect your iOS device
3. Build and run (Cmd+R)

### Option 2: AltStore (No Mac Required)

[AltStore](https://altstore.io/) allows sideloading apps using a free Apple ID:

1. Install AltStore on your device
2. Download the source and build an IPA, or wait for community builds
3. Open the IPA with AltStore

**Note:** Free Apple ID certificates expire every 7 days - AltStore auto-refreshes them.

### Option 3: TestFlight (Coming Soon)

We're working on TestFlight distribution for easier installation. Join the waitlist at [pars.network](https://pars.network).

### Why No Direct Download?

Apple requires all iOS apps to be cryptographically signed. Unlike Android, there's no way to install unsigned apps. Options are:
- **App Store** - Requires Apple review (in progress)
- **TestFlight** - For beta testing (coming soon)
- **AltStore** - Self-signing with your Apple ID
- **Build from source** - Full control

## Architecture

```
Pars Messenger iOS
├── Session/               # Main app target
├── SessionMessagingKit/   # Message handling, encryption
├── SessionNetworkingKit/  # Network layer (LibSession)
├── SessionUtilitiesKit/   # Shared utilities
└── SessionUIKit/          # UI components

Network Layer
└── libsession-util (C++ via Swift/ObjC bindings)
    └── Network endpoints (needs configuration for Pars)
```

## Pars Ecosystem

| Repository | Description |
|------------|-------------|
| [parsdao/pars-ios](https://github.com/parsdao/pars-ios) | iOS client (this repo) |
| [parsdao/pars-desktop](https://github.com/parsdao/pars-desktop) | Desktop client |
| [parsdao/pars-android](https://github.com/parsdao/pars-android) | Android client |
| [parsdao/pars-libsession](https://github.com/parsdao/pars-libsession) | Native crypto library |
| [parsdao/node](https://github.com/parsdao/node) | Pars blockchain node |

## Features

- End-to-end encryption (post-quantum)
- Decentralized message storage
- Onion routing for privacy
- Disappearing messages
- Group chats
- Voice messages
- Photo/file sharing

## Key Files

| File | Description |
|------|-------------|
| `SessionNetworkingKit/SessionNetwork/SessionNetwork.swift` | Network API config |
| `SessionNetworkingKit/LibSession/LibSession+Networking.swift` | LibSession integration |
| `SessionUtilitiesKit/General/Feature.swift` | Feature flags |
| `Session/Meta/SessionApp.swift` | App entry point |

## Contributing

1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Resources

- **Website:** [pars.network](https://pars.network)
- **Documentation:** [docs.pars.network](https://docs.pars.network)
- **PIPs:** [github.com/parsdao/pips](https://github.com/parsdao/pips)

## License

GPL-3.0 - See [LICENSE](LICENSE)

## Acknowledgments

- Fork of [Session iOS](https://github.com/session-foundation/session-ios)
- Built on [Lux Network](https://lux.network) technology
