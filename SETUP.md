# Build Presenter on GitHub

## Files in this folder
- `.github/workflows/desktop.yml`  builds Windows (.exe) and macOS (.dmg, Intel + Apple Silicon)
- `.github/workflows/android.yml`  builds the Android remote app (APK)
- `mobile/`                        the Android app (Capacitor): scan QR -> opens the computer's /remote page
- `package-build-section.json`     what to merge into your existing package.json
- `.gitignore`

## One-time setup
1. Copy these files into the ROOT of your project (next to `main.js` and `package.json`).
2. Merge `package-build-section.json` into your `package.json` (keep your own `main`, `version`, `dependencies`).
   `electron` must be in `devDependencies` (keep the version you already use).
3. Commit and push everything to https://github.com/mranandkumar4777/p1-app-pc
4. In GitHub: Settings -> Actions -> General -> Workflow permissions -> "Read and write permissions" -> Save.

## Run a build
- Easiest: Actions tab -> pick the workflow -> "Run workflow".
- Or release a version: raise "version" in package.json, then
  `git tag v1.0.1 && git push origin v1.0.1` (builds both).

## Where the files appear (Releases page)
- Windows / Mac installers + `desktop-version.json`: release **desktop-latest**
  (that is the UPDATE_INFO_URL in main.js)
- Android APK: release **mobile-latest**
  https://github.com/mranandkumar4777/p1-app-pc/releases/download/mobile-latest/PresenterRemote.apk

## Installing
- Android: open the APK link on the phone; allow "install unknown apps" when asked.
- Windows: Windows SmartScreen may warn (unsigned): More info -> Run anyway.
- Mac: unsigned: right-click the app -> Open the first time.
