# Marquee releases

Marquee is a native Android YouTube client: your own signed-in YouTube (Home, Subscriptions,
Library) in a native app, with background play, no ads and SponsorBlock.

This repository holds **only** what the app downloads to update itself:

- **Releases**: the signed APK for each version, with a `.sha256` checksum.
- **`ota/`**: the signed update config (`manifest.json` + `bundle-<version>.json`). It fixes
  YouTube breakages (client versions, keys, endpoints) without a new APK. Each bundle is signed
  with Ed25519 and the app rejects anything that does not verify.

There is no source code here.

## Install

1. On your Android phone (Android 8 or newer), open the
   [latest release](https://github.com/ap9400/Marquee-releases/releases/latest) and download
   `marquee-<version>-<code>.apk`.
2. Open the file. If Android asks, allow your browser or file manager to install unknown apps.
3. Tap **Install**. Google Play Protect doesn't know this app, so it may say **"App blocked to
   protect your device"**. Tap **More details → Install anyway**. (Some phones instead show
   "App scan recommended": tap **More details → Install without scanning**, or **Scan app**,
   which uploads it to Google.)
4. Open Marquee and sign in with your Google account.

Optional: check the download against the `.sha256` file from the same release
(`sha256sum -c marquee-<version>-<code>.apk.sha256`).

## Updates

Updates arrive in the app. Marquee checks this repository when it starts (and from
**Settings → Check for updates**), offers a new version, downloads and verifies it, and then
Android asks you to confirm the update (the first time, it asks you to allow Marquee to install
apps, and Play Protect may show the same "Install anyway" step as above). Your sign-in and
downloads are kept.

Config fixes in `ota/` apply on their own, within a few hours or at the next start.
