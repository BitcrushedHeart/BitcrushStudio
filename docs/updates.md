# Updates

Bitcrush Studio updates itself from this repository's
[Releases](https://github.com/BitcrushedHeart/BitcrushStudio/releases) page.

## How it works

- **At launch**, Studio quickly checks for a new version on the splash screen. If one is
  available it downloads with visible progress and applies **before the app opens**, so
  you're always launching the version you just saw released.
- The check is strictly time-boxed: if you're **offline** or the check is slow, Studio
  simply starts the current version. An update can never stop the app from launching.
- During a slow download a **Skip** option appears — skipping starts the current version
  and quietly finishes the update in the background for next time.
- Every downloaded update is **integrity-verified** (SHA-512 from the release manifest)
  before it is applied.

## Controls

- *Settings → General*: **"Automatically download and install updates on launch"**
  (on by default) and a **"Check for updates now"** button showing your current version
  and the result.
- With automatic updates off, updates found by a manual check apply the next time you
  quit.

## Windows and Linux

Both installers update the same way — Windows via the NSIS updater, Linux via the
AppImage updater. Releases always publish both platforms together at the same version.
