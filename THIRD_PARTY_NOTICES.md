# Third-Party Notices — Bitcrush Studio

Bitcrush Studio is proprietary software. It bundles, or installs at first launch,
the third-party open-source components listed below. Each remains under its own
license; this file provides the attributions those licenses require. Items
marked **⚠️ BLOCKED** have a confirmed licensing conflict that must be resolved
before that component ships in a commercial release — see the internal
`docs/LICENSING_CLEARANCE.md` for the full clearance ledger and evidence trail.

> Regenerate when dependencies change (the release build can refresh this from
> `backend/requirements-*.txt` and `frontend/package.json`). This file is not
> stamped by `scripts/release_stamp.py` — it carries no app version number, so
> it can't drift from the stamped release version.

---

## 1. Backend runtime — bundled in the frozen backend (base stack)

These ship inside the packaged `backend` executable (`requirements-global.txt`).

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
| SciPy (via reverse-geocode) | BSD-3-Clause |
| opencv-python-headless (OpenCV) | Apache-2.0 |
| PyExifTool (python bindings) | Dual BSD-3-Clause / GPL-3.0-or-later — distributed under the **BSD-3-Clause** terms |
| piexif | MIT |
| reverse-geocode | LGPL (self-declared by upstream, version unspecified — see note below) — used unmodified |
| imageio-ffmpeg (python wrapper) | BSD-2-Clause |
| py-spy | MIT |

**reverse-geocode (`reverse_geocode` 1.6.6):** upstream (`richardpenman/reverse_geocode`)
declares `license="lgpl"` in `setup.py` and carries the PyPI classifier
"License :: OSI Approved :: GNU Library or Lesser General Public License (LGPL)",
but ships **no `LICENSE` file** in its sdist, wheel, or GitHub repo, and does not
pin an LGPL version (GitHub's own license detector returns none, because there is
no recognized license file to detect). Verified 2026-07-12 against PyPI, the
installed `reverse_geocode-1.6.6.dist-info/METADATA`, and the upstream GitHub
repo/API. Absent an upstream-specified version, we comply with the stricter of
the two commonly-intended versions (LGPL-2.1-or-later terms). The package is
pure Python (no compiled extension), imported unmodified as an ordinary
dependency, and is not statically linked into any binary — a user can replace
the installed `reverse_geocode` module (source is trivially available on PyPI
and GitHub) without needing anything from us, which satisfies the LGPL's
user-relinking/modification intent. See `docs/LICENSING_CLEARANCE.md` for the
full evidence trail. Not blocked for commercial distribution.

**GeoNames data (reverse-geocode):** the offline reverse-geocoder bundles a
GeoNames *cities1000* dataset, licensed **CC BY 4.0**. Attribution: "This product
uses data from GeoNames (https://www.geonames.org/), licensed under CC BY 4.0."

**Bundled CPython runtime:** the installer ships an embedded CPython 3.11
runtime, © Python Software Foundation, under the PSF License Agreement. The full
license text (`LICENSE.txt`) is included alongside the bundled runtime.

## 2. Standalone downloader tools — separate frozen executables

The Dataset Builder ships two third-party command-line tools as **standalone
frozen executables** (see `tools.spec`). They are separate programs: Bitcrush
Studio invokes them as external processes over their public command-line
interfaces and does not link against them.

| Tool | License | Notes |
|---|---|---|
| **gallery-dl** | **GPL-2.0-only** | Shipped unmodified (v1.32.3). © Mike Fährmann and contributors. |
| **yt-dlp** | Unlicense (public domain) | Shipped unmodified. |

**gallery-dl source availability (GPL-2.0 §3):** gallery-dl is distributed
unmodified. Its complete corresponding source code is available at
<https://github.com/mikf/gallery-dl> (the exact shipped version is tagged there
and on PyPI). On request we will also provide the corresponding source for the
version shipped with any release: open an issue on the public repository. A copy
of the GNU General Public License v2.0 is available at
<https://www.gnu.org/licenses/old-licenses/gpl-2.0.html> and accompanies the
tool's source distribution.

## 3. Backend ML stack — installed at first launch into `data/gpu_env`

These are downloaded onto the user's machine during GPU setup
(`requirements-cuda.txt` + PyTorch). They are **not** redistributed inside the
installer; the installer fetches them from PyPI / the PyTorch index at the user's
direction.

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
| MANIQA (ported into `bitcrush_pyshared.quality`) | Apache-2.0 — model architecture ported from https://github.com/IIGROUP/MANIQA @ f573d862; KonIQ-10k weights downloaded from the authors' own release (https://github.com/IIGROUP/MANIQA/releases/download/Koniq10k/ckpt_koniq10k.pt, SHA-256 `a207f8ab57322e6be38ff5c8d019301dc032b454bef21c3c9f9dbf7974eebff6`). Replaces the former non-commercial pyiqa dependency. |

## 4. Native binaries

Studio ships **two independent FFmpeg builds** with different licenses and
different integration patterns — they must be evaluated separately.

| Component | License | Notes |
|---|---|---|
| FFmpeg (bundled inside `imageio-ffmpeg`, invoked as a separate process) | **GPL-3.0-or-later** | Video transcode + codec probe (`backend/video_transcode.py`); see §4a |
| FFmpeg (bundled inside `opencv-python-headless` / `cv2`, loaded in-process) | **LGPL** (decode-only; no GPL x264/x265 encoder) | All in-process video decode/metadata: `Tools/VideoScreenshotterEngine.py`, `backend/indexing_service.py`, `backend/dataset_cleaner_router.py`; see §4b |
| ExifTool | Perl Artistic / GPL-1.0+ | System dependency, invoked as a separate process; not bundled |

### 4a. `imageio-ffmpeg`'s bundled `ffmpeg.exe` — GPL-3.0-or-later, not blocked

Verified 2026-07-12 by running the installed binary
(`imageio_ffmpeg-0.6.0`'s `binaries/ffmpeg-win-x86_64-v7.1.exe`) with `-version`:
it identifies itself as `ffmpeg version 7.1-essentials_build-www.gyan.dev` with
configuration flags including `--enable-gpl --enable-version3 --enable-libx264
--enable-libx265 …` — a [gyan.dev](https://www.gyan.dev/ffmpeg/builds/) static
"essentials" build, which gyan.dev documents as **GPLv3**. `imageio-ffmpeg`'s own
license (BSD-2-Clause) covers only its thin Python wrapper; the bundled
executable carries its own, separate GPL-3.0 license.

Studio only ever invokes this binary as a **separate child process** over its
public command-line interface (`get_ffmpeg_exe()` → `subprocess` in
`backend/video_transcode.py`) — it is never imported, statically linked, or
compiled against. This is the same "mere aggregation via CLI" pattern already
used for gallery-dl (§2) and is compliant with GPL distribution: no code from
Bitcrush Studio is combined with FFmpeg's GPL code into a single binary.

**Source availability (GPL-3.0 §6):** this build is produced unmodified from
the public gyan.dev build scripts (https://github.com/GyanD/codexffmpeg) against
unmodified upstream FFmpeg source (https://github.com/FFmpeg/FFmpeg, tag
`n7.1`). On request we will identify the exact shipped build and point to its
corresponding public source. A copy of the GNU General Public License v3.0 is
available at <https://www.gnu.org/licenses/gpl-3.0.html>.

### 4b. OpenCV's bundled FFmpeg shared library — LGPL, not blocked

**Resolution of the former PyAV blocker (ISSUE-0335).** Studio previously loaded
PyAV (`av`) in-process for fast video seek/probe; PyAV 17.1.0 bundled an FFmpeg
8.1.1 build with a **functioning GPL `libx264` encoder compiled in**
(`av.codec.Codec("libx264", "w")` succeeded), which — loaded in-process and
frozen into `backend.exe` (linking, not subprocess aggregation) — was
GPL-incompatible with the proprietary backend and blocked the commercial launch.

**PyAV has been removed entirely.** It is no longer a dependency (dropped from
`apps/studio/pyproject.toml` and `uv.lock`), no Studio backend module imports
`av`, and `backend.spec` both stops collecting PyAV's DLLs and lists `av` in its
PyInstaller `excludes` so no transitive optional import can re-introduce them.
A regression test (`apps/studio/tests/backend/test_no_pyav_in_backend.py`)
enforces this.

All **in-process** video decode/metadata now runs through **OpenCV's** bundled
FFmpeg (`cv2`, `opencv-python-headless` — already shipped, Apache-2.0 wrapper),
used in `Tools/VideoScreenshotterEngine.py` (frame extraction + probe),
`backend/indexing_service.py` (metadata), and `backend/dataset_cleaner_router.py`
(dimensions). Video **codec probing** for the transcode path
(`backend/video_transcode.py`) parses the output of the already-cleared
`imageio-ffmpeg` `ffmpeg.exe` run as a **separate subprocess** (§4a).

OpenCV's bundled FFmpeg is **genuinely LGPL** — decode-only, with no GPL
encoders. Verified 2026-07-12 against the installed
`cv2/opencv_videoio_ffmpeg4130_64.dll`:

- The embedded configure string contains **no `--enable-gpl`**, **no
  `--enable-version3`**, and **no `libx264`/`libx265`** (grepped from the DLL
  bytes). It is built with LGPL-compatible codecs only (`--enable-libopenh264`,
  `--enable-libvpx`, `--enable-libaom`, VP8/VP9).
- H.264 **encoding is empirically unavailable**: `cv2.VideoWriter` with the
  `avc1` / `H264` / `x264` fourccs fails to open (it can only fall back to the
  optional, separately-downloaded Cisco OpenH264 runtime, which is not bundled).
- Decoding of H.264/HEVC/VP9/etc. works normally, which is all Studio needs
  in-process — encoding is handled exclusively by the GPL `ffmpeg.exe`
  subprocess (§4a), which is compliant as mere aggregation.

An LGPL decode-only FFmpeg linked in-process is compatible with proprietary
distribution (OpenCV ships it under exactly this arrangement). Not blocked for
commercial distribution. See `docs/LICENSING_CLEARANCE.md` for the full evidence
trail.

## 5. Adapted / vendored open-source code

| Origin | License | Use |
|---|---|---|
| **JoyTag** (`fpgaminer/joytag`, commit `ce0c4a4`) | Apache-2.0 | Model definition vendored verbatim in `Tools/joytag_vendored/` with the full Apache-2.0 license text and an attribution record. |
| **OneTrainer** (`Nerogar/OneTrainer`) | MIT — © Nerogar and contributors | Aspect-ratio bucketing resolution math adapted in `backend/onetrainer_buckets.py`. |
| **GeoCalib** (`cvg/GeoCalib`, commit `97b8968`) | Apache-2.0 | Inference subset (camera/gravity/perspective-field/LM-optimizer modules) vendored into `bitcrush_pyshared.geometry.geocalib` for camera-pitch / shot-angle estimation; heavy deps (cv2/kornia/torchvision/matplotlib) removed, image IO switched to Pillow. |

## 6. ML model weights

Model weights are downloaded on demand from their sources (e.g. Hugging Face)
at the user's direction and are **not** bundled in the installer. VLM / LLM
weights the user selects for captioning run through standard loaders
(`transformers`, `llama-cpp-python`). Each model is governed by its own
license, which applies to the user's use of it — review the model card before
commercial use. Licenses for the models Bitcrush Studio offers by default:

- Microsoft **Florence-2** (OCR/caption) — MIT
- **SmilingWolf WD** taggers — Apache-2.0
- **JoyTag** (fancyfeast/joytag) — Apache-2.0
- **GeoCalib** pinhole weights (cvg/GeoCalib) — CC-BY-4.0; used by `bitcrush_pyshared.geometry` for camera-pitch estimation, downloaded from https://github.com/cvg/GeoCalib/releases/download/v1.0/geocalib-pinhole.tar (SHA-256 `86d6aeacd8bbd974c59ce39f61854e00d36911c732ad89be471476fd708722ac`)

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
