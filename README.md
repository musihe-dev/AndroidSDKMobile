# Android SDK Mobile — Preview 0.1.0

Native Android application starter for importing and inspecting an Android SDK `.tar.xz` archive.

## Current functionality
- Native Android activity (Java).
- Uses Android Storage Access Framework to select an archive.
- Reads XZ-compressed TAR archives and displays entry names and sizes.
- Displays an explicit Linux-musl vs Android-Bionic compatibility warning.

## Important limitations
This is **not yet a functioning Android SDK runtime** and it does not execute ADB/AAPT/SDK Manager.
The supplied archive contains Linux ARM64/musl executables. Android uses Bionic and has different
system interfaces and sandbox restrictions. A static ELF binary is not automatically Android-compatible.
The archive inspected for this project did not include an Android NDK or `android.jar` platform package.

## Build
1. Open this folder in Android Studio (a recent version).
2. Allow Gradle to download the Android Gradle Plugin and dependencies.
3. Install Android SDK Platform 35 through SDK Manager.
4. Connect an Android device with USB debugging enabled, or use an emulator.
5. Select **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

The APK output is normally under `app/build/outputs/apk/debug/app-debug.apk`.

## Next porting stages
1. Extract and inventory the archive.
2. Test each ELF executable on Android ARM64.
3. Obtain Android NDK and rebuild incompatible components from source where licensing/source permits.
4. Implement native tool execution safely within app-private storage.
5. Add SDK platform packages and a build pipeline, then sign and test a release APK.
