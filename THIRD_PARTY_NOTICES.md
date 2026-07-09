# Third-Party Notices — Bitcrush Studio

Bitcrush Studio is proprietary software (see `LICENSE` and `EULA.md`). It
bundles, or installs at first launch, the third-party open-source components
listed below. Each remains under its own license; this file provides the
attributions those licenses require. Licenses marked **⚠️ verify** are pending
final confirmation.

---

## 1. Backend runtime — bundled in the frozen backend (base stack)

These ship inside the packaged `backend` executable.

| Component | License |
|---|---|
| FastAPI | MIT |
| Starlette | BSD-3-Clause |
| Uvicorn | BSD-3-Clause |
| Pydantic | MIT |
| python-multipart | Apache-2.0 |
| watchdog | Apache-2.0 |
| aiofiles | Apache-2.0 |
| websocket-client | Apache-2.0 |
| psutil | BSD-3-Clause |
| blake3 (python) | CC0-1.0 OR Apache-2.0 |
| cryptography | Apache-2.0 OR BSD-3-Clause |
| requests | Apache-2.0 |
| rapidfuzz | MIT |
| Pillow | MIT-CMU (HPND) |
| NumPy | BSD-3-Clause |
| SciPy | BSD-3-Clause |
| opencv-python-headless (OpenCV) | Apache-2.0 |
| PyExifTool (python bindings) | Dual BSD-3-Clause / GPL-3.0-or-later — distributed under the **BSD-3-Clause** terms |
| piexif | MIT |
| reverse-geocode | LGPL (per package metadata) — used unmodified — ⚠️ verify |
| imageio-ffmpeg (python wrapper) | BSD-2-Clause |
| PyAV (av) | BSD-3-Clause |
| py-spy | MIT |

**GeoNames data (reverse-geocode):** the offline reverse-geocoder bundles a
GeoNames *cities1000* dataset, licensed **CC BY 4.0**. Attribution: "This product
uses data from GeoNames (https://www.geonames.org/), licensed under CC BY 4.0."

**Bundled CPython runtime:** the installer ships an embedded CPython 3.11
runtime, © Python Software Foundation, under the PSF License Agreement. The full
license text (`LICENSE.txt`) is included alongside the bundled runtime.

## 2. Standalone downloader tools — separate frozen executables

Bitcrush Studio's Dataset Builder ships two third-party command-line tools as
**standalone frozen executables**. They are separate programs: Bitcrush Studio
invokes them as external processes over their public command-line interfaces and
does not link against them.

| Tool | License | Notes |
|---|---|---|
| **gallery-dl** | **GPL-2.0-only** | Shipped unmodified (v1.32.3). © Mike Fährmann and contributors. |
| **yt-dlp** | Unlicense (public domain) | Shipped unmodified. |

**gallery-dl source availability (GPL-2.0 §3):** gallery-dl is distributed
unmodified. Its complete corresponding source code is available at
<https://github.com/mikf/gallery-dl> (the exact shipped version is tagged
there and on PyPI). On request we will also provide the corresponding source
for the version shipped with any release: open an issue on this repository.
A copy of the GNU General Public License v2.0 is available at
<https://www.gnu.org/licenses/old-licenses/gpl-2.0.html> and accompanies the
tool's source distribution.

## 3. Backend ML stack — installed at first launch into the local GPU environment

These are downloaded onto the user's machine during GPU setup. They are **not**
redistributed inside the installer; the app fetches them from PyPI / the PyTorch
index at the user's direction.

| Component | License |
|---|---|
| PyTorch, torchvision | BSD-3-Clause |
| transformers | Apache-2.0 |
| huggingface_hub | Apache-2.0 |
| datasets | Apache-2.0 |
| accelerate | Apache-2.0 |
| safetensors | Apache-2.0 |
| timm | Apache-2.0 |
| open-clip-torch | MIT |
| einops | MIT |
| onnxruntime-gpu | MIT |
| llama-cpp-python | MIT |
| optimum-quanto | Apache-2.0 |
| hqq | Apache-2.0 |
| pandas | BSD-3-Clause |
| pyarrow (Apache Arrow) | Apache-2.0 |
| pyiqa (IQA-PyTorch) | CC BY-NC-SA 4.0 + S-Lab License 1.0 (**non-commercial**) — ⚠️ under review |
| insightface (code) | MIT — model weights ⚠️ verify (non-commercial) |

## 4. Native binaries

| Component | License | Notes |
|---|---|---|
| FFmpeg (via imageio-ffmpeg / PyAV) | LGPL-2.1+ or GPL — ⚠️ verify build | Used for video transcode/decode |
| ExifTool | Perl Artistic / GPL-1.0+ | System dependency, invoked as a separate process; not bundled |

## 5. Adapted / vendored open-source code

| Origin | License | Use |
|---|---|---|
| **JoyTag** (`fpgaminer/joytag`, commit `ce0c4a4`) | Apache-2.0 | Model definition vendored verbatim; the full Apache-2.0 license text and an attribution record ship with the copy. |
| **OneTrainer** (`Nerogar/OneTrainer`) | MIT — © Nerogar and contributors | Aspect-ratio bucketing resolution math adapted for export bucketing. |

## 6. ML model weights

Model weights are downloaded on demand from their sources (e.g. Hugging Face)
and are **not** bundled in the installer. Each weight carries its own license;
the ones intended for use include (licenses ⚠️ to verify per model):

- Microsoft **Florence-2** (OCR/caption) — MIT
- **SmilingWolf WD** taggers — Apache-2.0
- **JoyTag** (fancyfeast/joytag) — Apache-2.0
- **InsightFace** detection/recognition packs — ⚠️ verify (non-commercial)
- JoyCaption / VLMs — ⚠️ verify

Excluded from public builds: the former object-detection stack and associated
weights are intentionally not distributed in Bitcrush Studio 1.0.0.

## 7. Frontend (Electron app)

| Component | License |
|---|---|
| Electron | MIT |
| electron-updater, electron-builder | MIT |
| React, React-DOM | MIT |
| Vite | MIT |
| Tailwind CSS | MIT |
| TypeScript | Apache-2.0 |
| lucide-react | ISC |
| react-markdown, remark-gfm | MIT |
| react-virtuoso | MIT |
| sass | MIT |

**Fonts:** the UI loads **DM Sans** and **JetBrains Mono** from Google Fonts at
runtime. Both are licensed under the SIL Open Font License 1.1; they are not
redistributed with the app.

## 8. Entitlement worker

| Component | License |
|---|---|
| @noble/ed25519, @noble/hashes | MIT |
| wrangler (dev only) | Apache-2.0 / MIT |

---

*This notice is provided to satisfy attribution requirements of the licenses
above. It is not a grant of rights to Bitcrush Studio itself, which remains
proprietary (see `EULA.md`).*
