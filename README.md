# Bitcrush Studio

**Bitcrush Studio is a desktop application for managing large image–caption
datasets**.

Captioning, labelling, masking, and scoring images - made easy.

---

## What it does

Bitcrush Studio brings the repetitive parts of dataset preparation into one
fast, local, GPU-aware workflow:

- **Tagging** — automatic image tagging with multiple models, plus bulk
  find-and-replace and tag normalisation.
- **Captioning** — review, edit, and reconcile captions with a workflow built
  for fast human verification rather than blind trust in model output.
- **Masking & editing** — region masking, watermark handling, letterbox
  cropping, and image manipulation.
- **Deduplication** — detect and remove duplicate and near-duplicate images.
- **People & location** — optional people scanning and offline EXIF-based
  location tagging.
- **Dataset building** — import and organise media with its metadata.
- **Quality tools** — surface low-quality and problematic files.

Everything runs on your own machine; your images and captions stay local.

## Platform

- **Windows** (installer) and **Linux** (AppImage) desktop application — both
  published together on each release.
- Uses your local GPU where available (an ML/GPU stack is downloaded to your
  device during setup, at your direction). CPU-only mode is fully supported.

## Installation

Download the latest build from the
[**Releases**](https://github.com/BitcrushedHeart/BitcrushStudio/releases) page
and run it. Release notes accompany each version.

> Builds are not yet code-signed, so Windows SmartScreen may warn on first run —
> **More info → Run anyway**. Details in the [installation guide](docs/installation.md).

Bitcrush Studio was written in Python & Typescript - no vulnerabilities are shipped with a release.

## Documentation

- [Installation](docs/installation.md) — Windows & Linux, system requirements,
  SmartScreen, uninstalling.
- [First-time setup](docs/first-run-setup.md) — the setup flow, GPU acceleration
  options, re-running setup / repair.
- [Updates](docs/updates.md) — how auto-update works and how to control it.
- [Troubleshooting](docs/troubleshooting.md) — logs, common issues, filing a
  good bug report.

## License

Bitcrush Studio is proprietary. Use of the application is governed by its End
User License Agreement, included with each build. The application bundles
third-party open-source components, each under its own license, with
attributions provided alongside the build.

© Bitcrush Studio. All rights reserved.

## Support

Questions, bug reports, and feature requests are welcome via this repository's
**Issues** page.
