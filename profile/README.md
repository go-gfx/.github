<p align="center"><img src="https://raw.githubusercontent.com/go-gfx/brand/main/social/go-gfx.png" alt="go-gfx" width="720"></p>

# go-gfx

🌐 **[Website](https://go-gfx.github.io)** · 📚 **[Documentation](https://go-gfx.github.io/docs/)**

[![License](https://img.shields.io/badge/license-BSD--3--Clause-blue.svg)](https://github.com/go-gfx/gfx/blob/main/LICENSE)
[![Website](https://img.shields.io/badge/website-go--gfx.github.io-0891b2)](https://go-gfx.github.io)
[![Docs](https://img.shields.io/badge/docs-mkdocs--material-0891b2)](https://go-gfx.github.io/docs/)
[![Pure Go](https://img.shields.io/badge/pure%20Go-CGO%3D0-00ADD8?logo=go&logoColor=white)](https://github.com/go-gfx/gfx)

**The pure-Go, CGO=0 2D graphics foundation** — the shared substrate that sits
*below* the fleet's image-processing and rendering libraries. The Go answer to
what Skia, Cairo and `image/draw` provide elsewhere: pixel buffers, colour
science, high-quality resampling, image codecs and a vector rasterizer, each
usable on its own, with **no third-party dependencies**.

go-gfx is **not** an image-processing library (that is
[go-images](https://github.com/go-images/images), the scikit-image analogue) and
**not** a widget toolkit (that is [go-widgets](https://github.com/go-widgets)).
It is the common layer both stand on, so colour blending, resampling, codecs and
path rasterization are written and tested **once** and shared across the whole
ecosystem.

## Repositories

| Repo | What it is |
|------|------------|
| [**gfx**](https://github.com/go-gfx/gfx) | the library: `geometry` · `color` · `raster` · `resample` · `codec` · `vector` in one CGO=0 module |
| [**docs**](https://github.com/go-gfx/docs) | MkDocs Material documentation, served at [/docs/](https://go-gfx.github.io/docs/) |
| [**go-gfx.github.io**](https://github.com/go-gfx/go-gfx.github.io) | the Hugo landing page |
| [**brand**](https://github.com/go-gfx/brand) | brand assets — logos & icons |

## Packages

| Package | Purpose |
|---------|---------|
| `geometry` | points, rectangles, affine transforms |
| `color`    | RGB/XYZ/Lab, sRGB↔linear, premultiplied alpha, blend modes |
| `raster`   | shared pixel-buffer / pixel-format substrate |
| `resample` | box/area, bicubic (Catmull-Rom), Lanczos resizing |
| `codec`    | PNG, JPEG, WebP, ICO, ICNS, GIF, TIFF decoders/encoders |
| `vector`   | paths, anti-aliased rasterizer, strokes, gradients |

## Consumers

- [**go-images**](https://github.com/go-images/images) — image processing, on `raster`/`color`/`resample`.
- [**go-widgets**](https://github.com/go-widgets)/painter — tri-backend renderer, on `vector`/`raster`/`color`.
- [**go-webengine**](https://github.com/go-webengine) — HTML/CSS → image, on `resample`/`codec`/`vector`.
- [**go-widgets**](https://github.com/go-widgets)/desktop — icon & thumbnail rendering.

## Principles

- **Pure Go, `CGO_ENABLED=0`.** No Skia, no Cairo, no native shims.
- **Zero third-party dependencies.** Nothing fleet-side except
  [go-asmgen](https://github.com/go-asmgen) for optional SIMD, pulled in only at
  code-generation time so the library keeps a zero-dependency `go.mod`.
- **100% test coverage**, including error branches, gated in CI.
- **Six architectures.** Build + test on all six of Go's 64-bit targets —
  amd64 / arm64 natively, loong64 / riscv64 / ppc64le / s390x under qemu.
- **BSD-3-Clause** on every source file.

## Status

Bootstrapping. The module skeleton is up; packages land incrementally, starting
with `resample`, `raster` and `color`. See the
[roadmap](https://go-gfx.github.io/docs/latest/roadmap/).
