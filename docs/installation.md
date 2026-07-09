# Installing Bitcrush Studio

Bitcrush Studio ships as a **Windows installer** and a **Linux AppImage**. Both are
published together on the [Releases](https://github.com/BitcrushedHeart/BitcrushStudio/releases)
page for each version.

## Windows

1. Download `Bitcrush Studio Setup <version>.exe` from the latest release.
2. Run it. Because builds are not yet code-signed, **Windows SmartScreen** may show
   "Windows protected your PC" — click **More info → Run anyway**. This is expected for
   an independent release; the download's integrity is still verified by the built-in
   updater on every subsequent update.
3. The installer is a small per-user setup (no administrator rights needed). You can
   change the install folder; system-owned locations like `Program Files` are
   deliberately not allowed.
4. When it finishes, Studio launches straight into [first-time setup](first-run-setup.md).

Your data (databases, settings, downloaded models) is **not** stored in the install
folder — it lives in your user profile and **survives uninstall and reinstall**.

## Linux

1. Download `Bitcrush Studio-<version>.AppImage` from the latest release.
2. Make it executable and run it:

   ```bash
   chmod +x "Bitcrush Studio-<version>.AppImage"
   ./"Bitcrush Studio-<version>.AppImage"
   ```

3. First launch enters the same [first-time setup](first-run-setup.md) as Windows,
   including the license agreement.

The AppImage is self-contained (it bundles its own Python runtime); no system Python or
other packages are required.

## System requirements

| | Minimum | Recommended |
|---|---|---|
| OS | Windows 10/11 x64, or a modern x64 Linux distribution | — |
| GPU | None (CPU-only mode is fully supported) | NVIDIA GPU with current drivers |
| Disk | ~2 GB for the application | +up to ~10 GB if you enable GPU acceleration (the ML stack downloads during setup) |

AMD GPUs: ROCm on Linux is available as a best-effort option; AMD on Windows is
experimental. Setup always offers a working CPU-only fallback.

## Uninstalling

- **Windows:** uninstall from Windows Settings / the Start Menu entry. Your data stays
  in your user profile; reinstalling later finds it again.
- **Linux:** delete the AppImage. Your data directory is untouched.
