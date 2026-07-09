# Troubleshooting

## Where the logs are

Everything Studio writes lives under your data directory (chosen during setup;
defaults to your user profile):

| File | What it covers |
|---|---|
| `logs/setup.log` | First-time setup and GPU-stack installs — a failed install always leaves diagnostics here |
| `logs/backend.log` | The application backend at runtime |

The setup error screen has **Copy log** / **Open log folder** buttons; please attach the
relevant log when filing an issue.

## Common issues

### "Windows protected your PC" when running the installer
Expected — builds are not yet code-signed. Click **More info → Run anyway**. See
[Installation](installation.md).

### Antivirus flags the installer or app
Unsigned installers occasionally trip AV heuristics as false positives. Each release is
checked before publishing; if your AV quarantines a file, restore/allow it or report it
to us via Issues with the AV product name.

### GPU install failed or GPU features stopped working
1. Open *Settings → System* — it shows the GPU environment status and offers
   **Install / Verify / Repair** actions in-app.
2. If the app itself won't start, re-run setup instead: on Windows re-run the installer
   (or the "Setup (repair)" Start Menu shortcut); on Linux launch the AppImage with
   `--setup`. Choose **Install/repair GPU acceleration**.
3. Verification is honest: if your hardware can't run the accelerated stack, setup will
   say so and offer CPU-only mode — every tool works without a GPU.

### Not enough disk space for GPU acceleration
CUDA variants need up to ~10 GB during install. Setup checks before downloading and
tells you how much is needed. Free space or choose CPU-only, then repair later.

### The app won't start
- Launch setup in repair mode (see above) and run **Repair installation**.
- Check `logs/backend.log` for the failure.
- Your data is safe: it lives outside the install folder and is never touched by
  reinstalling the application.

### Update seems stuck
The launch-time update check times out on its own and starts the current version — you
can also use the **Skip** button during a slow download. Updates can be turned off in
*Settings → General* and run manually instead.

## Filing a good issue

Open an issue on this repository with:
1. Your Studio version (shown in *Settings*, or the installer filename).
2. OS + GPU (if relevant).
3. What you did, what you expected, what happened.
4. The matching log snippet (`setup.log` for install problems, `backend.log` otherwise).
