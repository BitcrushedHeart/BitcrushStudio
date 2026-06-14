# Bitcrush Studio

**Bitcrush Studio is a desktop application for managing large image–caption
datasets** — built for collections ranging from a handful of images up to
millions of image–caption pairs, where a single image may carry multiple
captions.

It is **closed-source, proprietary software that is free to download**. This
repository hosts the project's public documentation only; the application
source is not published here.

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

## Editions

| Edition | How you get it | What you get |
|---|---|---|
| **Free** | Download and install | The full toolset that isn't flagged supporter-only |
| **Supporter** | Link an active membership in-app | Everything in Free, plus any supporter-only tools |

Premium capability is unlocked at runtime by a membership link rather than by
shipping a separate paid build — one artifact to build, test, and update.

## Platform

- **Windows** desktop application.
- Uses your local GPU where available (an ML/GPU stack is downloaded to your
  device during setup, at your direction).

## Installation

Download the latest build from the **Releases** page and run the installer.
Release notes accompany each version.

## License

Bitcrush Studio is proprietary. Use of the application is governed by its End
User License Agreement, included with each build. The application bundles
third-party open-source components, each under its own license, with
attributions provided alongside the build.

© Bitcrush Studio. All rights reserved.

## Support

Questions, bug reports, and feature requests are welcome via this repository's
**Issues** page.
