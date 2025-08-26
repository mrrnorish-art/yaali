Video:

https://drive.google.com/file/d/1tscueU-NDw67WAJo31jLzIaoeoG3g7K6/preview

## Installation

- Download last release version
- Unzip XRay framework and paste into plugin_folder/ios

## Podfile
Open ios/Podfile and set the platform to iOS 15
```Podfile
# Uncomment this line to define a global platform for your project
platform :ios, '15.0'
```

```bash
cd ios/
pod install
```

## Xcode Setup

- Open Runner.xcworkspace with Xcode.

### Runner target
- Set the Minimum Deployment Target to iOS 15.
- Go to the Signing & Capabilities tab.
- Add the App Group capability.
- Add the Network Extension capability and activate Packet Tunnel.


### XrayTunnel target
- Add a Network Extension Target with the name __XrayTunnel__
- Set the Minimum Deployment Target to iOS 15.
- Add the App Group capability.
- Add the Network Extension capability and activate Packet Tunnel.

#### Add XrayTunnel dependencies
- Open the Runner project and go to the Package Dependencies tab.
- Add https://github.com/blueboy-tm/Tun2SocksKit to the XrayTunnel Target.
- Open the __General__ tab of the __XrayTunnel__ Target.
- Add __XRay.xcframework__ to Frameworks and Libraries.
- Add __libresolv.tbd__ to Frameworks and Libraries.


<br>

- Open ios/XrayTunnel/PacketTunnelProvider.swift.
- Paste the content of [this file](./example/ios/XrayTunnel/PacketTunnelProvider.swift).
- Open the Runner Target > Build Phases tab.
- Move __Embed Foundation Extensions__ to the bottom of __Copy Bundle Resources__.



## flutter
Pass the providerBundleIdentifier and groupIdentifier to the initializeV2Ray function:

``` dart
await flutterV2ray.initializeV2Ray(
    providerBundleIdentifier: "IOS Provider bundle indentifier",
    groupIdentifier: "IOS Group Identifier",
);
```