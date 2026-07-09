<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/wordmark-dark-bg.png" />
    <source media="(prefers-color-scheme: light)" srcset="assets/wordmark-light-bg.png" />
    <img src="assets/wordmark-light-bg.png" alt="Bitcrush Studio" width="560" />
  </picture>
</p>
<p align="center">
  <a href="https://www.patreon.com/cw/Bitcrushed_Heart">
    <img src="https://img.shields.io/badge/Patreon-Bitcrushed__Heart-bb00a1?style=flat&amp;logo=patreon&amp;logoSize=auto" alt="Patreon: Bitcrushed Heart">
  </a>
  <a href="https://civitai.red/user/BitcrushedHeart">
    <img src="https://img.shields.io/badge/Civitai%20Red-BitcrushedHeart-68005b?style=flat&amp;logo=robotframework&amp;logoSize=auto" alt="Civitai Red: BitcrushedHeart">
  </a>
</p>
  
<p align="center">
  Bitcrush Studio is a desktop app for building, captioning, cleaning, reviewing, and preparing large image–caption datasets.
</p>

## Features

### Build datasets
- Import from Hugging Face Datasets and supported websites.
- Extract frames from videos.
- Sort images into concepts.

### Caption and label
- Caption with local or API-based LLMs.
- Use WD Tagger and JoyTag models.
- Generate variations and metadata-aware prompts.

### Clean and curate
- Find duplicates using hashes, pHash, dHash, or embeddings.
- Detect broken images and poor-quality samples.
- Review, score, compare, and prune datasets.

### Prepare for training
- Convert, downscale, crop, rotate, and export images.
- Generate masks for masked diffusion training.

## Installation

Available for **Windows** (installer) and **Linux** (AppImage) — both published together on every release.

> [!IMPORTANT]
> **Note:** CUDA 13 is required for GPU features - update your GPU drivers to get the latest version of CUDA for PyTorch.
> AMD GPU support is _experimental_ and no assurances are given that it is fully functional at this stage.

### Automatic Installation

Just download the latest release via the [Releases tab](https://github.com/BitcrushedHeart/BitcrushStudio/releases) and run the installer - Bitcrush Studio will walk you through the rest of the process.

> [!NOTE]
> Builds aren't code-signed yet, so Windows SmartScreen may warn on first run — click **More info → Run anyway**.

More detail: [Installation](docs/installation.md) · [First-time setup](docs/first-run-setup.md) · [Updates](docs/updates.md) · [Troubleshooting](docs/troubleshooting.md)

## Updating

Bitcrush Studio will automatically update when a new version is released - you can disable this feature in the application settings.

## Bug Reporting & Feature Suggestions

Please raise any bugs or feature requests in the [Issues Tab](https://github.com/BitcrushedHeart/BitcrushStudio/issues) in GitHub.

## Summary & Credits

Thank you to everyone that has supported me during my time in the machine-learning community, particularly [dxqb](https://github.com/dxqb), [Koratahiu](https://github.com/Koratahiu), [O-J1](https://github.com/O-J1) and [caith-h](https://github.com/caith-h).

Thank you to all the researchers and developers that made Bitcrush Studio possible. 

**Made with <3 By BitcrushedHeart**

## License

Bitcrush Studio is proprietary software, free to download. Use is governed by the
End User License Agreement included with each build. Bundled third-party open-source
components remain under their own licenses, with attributions shipped alongside the app.

## Related Projects

[**Bitcrush Linki**](https://github.com/BitcrushedHeart/BitcrushLinki) - Chromium extension to copy a large number of links from your open tabs. Free & open source. 

[**OneTrainer**](https://github.com/Nerogar/OneTrainer) - For training diffusion models. Bitcrush Studio was built with OneTrainer support first.



