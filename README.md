# NoWakeProximity (LSPosed Module)

An LSPosed / Xposed module for Xiaomi HyperOS that prevents the device from immediately going back to sleep when waking up while the proximity sensor is covered (e.g. double-tap to wake in pocket or when hands are over the top bezel).

## Features
- Hooks `com.android.server.policy.BaseMiuiPhoneWindowManager.registerProximitySensor` to disable the wake proximity listener.
- Lightweight, zero bloat, native executable.
- Signed with debug key for seamless installation on rooted devices.

## Installation & Setup
1. Download `NoWakeProximity-release.apk` from the [Releases](https://github.com/) section.
2. Install the APK on your device.
3. Open **LSPosed Manager** > **Modules** tab.
4. Enable **NoWakeProximity**.
5. Ensure the scope is set to **System Framework** (`android`).
6. Reboot your device.
7. Verify LSPosed logs show: `NoWakeProximity: hooked registerProximitySensor`.

## Manual Build
To build locally with Gradle:
```bash
./gradlew assembleRelease
```
The compiled APK will be generated at:
```
app/build/outputs/apk/release/app-release.apk
```

## Automated GitHub Releases
This repository includes a GitHub Actions workflow (`.github/workflows/release.yml`) configured to:
- Automatically compile and verify builds on push.
- Automatically build and publish a GitHub Release with attached APKs whenever you push a version tag (e.g. `git tag v1.0.0 && git push origin v1.0.0`).
- Allow manual release triggering via the **Actions** tab using `workflow_dispatch`.
