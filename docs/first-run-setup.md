# First-time setup

The first launch opens Studio's branded setup — a short, resumable flow that runs
*before* the application itself. If anything is interrupted, relaunching picks up where
you left off.

## The steps

1. **License** — read and accept the End User License Agreement.
2. **System scan** — Studio detects your GPU, CPU, RAM, and free disk space and shows a
   hardware summary. Nothing is installed at this step.
3. **Choices**
   - **Data directory** — where databases, settings, and downloaded models live.
     Defaults to your user profile; changeable.
   - **GPU acceleration** — Studio recommends the right option for your hardware
     (e.g. a CUDA variant matched to your NVIDIA driver). You can also pick
     **CPU-only**, or **Skip for now** and set it up later from
     *Settings → System* or by re-running setup.
   - **Models cache** — where downloaded ML models are stored (defaults inside the
     data directory).
4. **Prepare** — folders and logging are set up; if you're upgrading from an older
   install, existing data is migrated.
5. **Install** *(only if you enabled GPU acceleration)* — the ML/GPU stack downloads to
   your machine with live progress (size, speed). Expect a multi-GB download and up to
   ~10 GB of peak disk use for CUDA variants; setup refuses to start the download if
   there isn't enough space, rather than failing halfway.
6. **Verify** — the installed stack is tested for real before being marked ready.
7. **Done** — Studio starts, and in-app onboarding takes over (preferences, adding your
   first dataset).

## GPU support tiers

| Hardware | Support |
|---|---|
| NVIDIA (CUDA) | Fully supported, auto-detected — the default path |
| AMD on Linux (ROCm) | Best-effort |
| AMD on Windows | Experimental, clearly labelled in setup |
| No GPU / skip | Fully supported — every tool has a CPU fallback |

If GPU verification fails, setup says so honestly and offers the CPU path — a failed
GPU install never blocks you from using the app.

## Re-running setup (repair / change settings)

- **Windows:** re-run the downloaded installer over an existing installation, or use the
  *"Bitcrush Studio Setup (repair)"* Start Menu shortcut. A maintenance menu offers:
  install/repair GPU acceleration, change data directory, repair installation.
- **Linux:** run the AppImage with the setup flag:

  ```bash
  ./"Bitcrush Studio-<version>.AppImage" --setup
  ```

- **In-app:** *Settings → System* can install or repair GPU acceleration without
  leaving Studio.

Because setup runs outside the main application, it works even when the app itself
won't start.
