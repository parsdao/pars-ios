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

## Building

### Prerequisites

- Xcode 15.0+
- iOS 15.0+ deployment target
- CocoaPods

### Build Steps

1. Clone the repository:
```bash
git clone https://github.com/parsdao/pars-ios
cd pars-ios
```

2. Install dependencies:
```bash
pod install
```

3. Open the workspace:
```bash
open Session.xcworkspace
```

4. Build and run in Xcode (Cmd+R)

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
