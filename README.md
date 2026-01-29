# Lux Messenger iOS

> Private messaging on the Lux Network - A fork of [Session iOS](https://github.com/session-foundation/session-ios)

## Overview

Lux Messenger iOS is a fork of Session iOS, intended to connect to the Lux Network's SessionVM instead of the Oxen network. This app provides end-to-end encrypted messaging with post-quantum cryptographic protection.

## Current Status

**Integration Status: In Progress**

The iOS app currently uses `libsession-util` for networking, which has hardcoded network endpoints. Full integration with the Lux SessionVM requires modifications to the underlying C++ library.

### What Works
- Building and running the app
- Core messaging functionality (against Session mainnet)

### What Needs Work
- Network configuration to connect to Lux SessionVM
- libsession-util modifications for custom network support
- Branding updates (Lux Messenger)

## Building

### Prerequisites

- Xcode 15.0+
- iOS 15.0+ deployment target
- CocoaPods

### Build Steps

1. Clone the repository:
```bash
git clone https://github.com/lux-tel/session-ios
cd session-ios
```

2. Install dependencies:
```bash
pod install
```

3. Open the workspace:
```bash
open Session.xcworkspace
```

4. Build and run in Xcode.

## Architecture

```
Session (iOS App)
├── SessionMessagingKit    # Message handling, encryption
├── SessionNetworkingKit   # Network layer (uses LibSession)
├── SessionUtilitiesKit    # Shared utilities
└── SessionUIKit           # UI components

SessionNetworkingKit
└── LibSession+Networking.swift
    └── libsession-util (C++ native library)
        └── Hardcoded network endpoints
```

## Configuration for Lux Network

### Current Limitation

The network configuration in iOS is handled by `libsession-util`, a C++ library with hardcoded endpoints:

```cpp
// In libsession-util/src/session_network.cpp
constexpr auto file_server = "filev2.getsession.org"sv;
```

### Planned Approach

To enable Lux network connectivity:

1. **Modify libsession-util** (`lux-tel/libsession-util`)
   - Add environment-based configuration
   - Support custom seed node URLs
   - Support custom file server URLs

2. **Update iOS integration**
   - Pass Lux network configuration to LibSession
   - Update UI branding

## Related Repositories

| Repository | Description |
|------------|-------------|
| [luxfi/session](https://github.com/luxfi/session) | Go SessionVM + API layer |
| [luxcpp/session](https://github.com/luxcpp/session) | C++ storage server |
| [lux-tel/libsession-util](https://github.com/lux-tel/libsession-util) | Native library (needs modification) |
| [lux-tel/session-desktop](https://github.com/lux-tel/session-desktop) | Desktop client (configured) |
| [lux-tel/session-android](https://github.com/lux-tel/session-android) | Android client |

## Development

### Key Files

| File | Description |
|------|-------------|
| `SessionNetworkingKit/SessionNetwork/SessionNetwork.swift` | Network API server config |
| `SessionNetworkingKit/LibSession/LibSession+Networking.swift` | LibSession integration |
| `SessionUtilitiesKit/General/Feature.swift` | Feature flags |
| `Session/Meta/SessionApp.swift` | App entry point |

### Debug Configuration

Feature flags can be enabled in developer settings for debugging:
- `forceOffline` - Test offline behavior
- `truncatePubkeysInLogs` - Privacy in debug logs

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

GPL-3.0 - Same as upstream Session iOS

## Upstream

This project is a fork of [Session iOS](https://github.com/session-foundation/session-ios) by the Session Technology Foundation.
