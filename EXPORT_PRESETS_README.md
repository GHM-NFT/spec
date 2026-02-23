# Export Presets — Cross‑Marketplace

These presets are practical defaults that render crisply on major NFT marketplaces (OpenSea, Foundation, Rarible, Magic Eden, Objkt, Manifold) while keeping file sizes efficient.

---

## 1) Item Artwork (Images)

**Preview (detail page / zoom) — choose the closest aspect ratio**
- **Square (1:1):** 1600×1600 px  *(option: 2048×2048 for extra detail)*
- **Landscape (16:9):** 1920×1080 px  *(alt: 1600×900)*
- **Portrait (3:4):** 1500×2000 px  *(alt: 1200×1600)*
- **Portrait (9:16):** 1080×1920 px

**Thumbnail (grid card)**
- **Square:** 512×512 px  *(always export a square thumb even for non‑square works)*
- **16:9:** 512×288 px
- **3:4:** 480×640 px
- **9:16:** 360×640 px

**Encoding**
- **Format:** JPG (sRGB), Quality **80–85** (target **< 1 MB** preview, **< 120 KB** thumbnail)
- **Color:** sRGB, embed profile
- **Metadata:** strip heavy EXIF to reduce size
- **Filenames:** `...-preview.jpg` (PREVIEWS), `...-thumb.jpg` (THUMBNAILS)

---

## 2) Item Video (Relics)

**Poster image (used as `image` in metadata)**
- Match the preview size above (e.g., 1600×1600 or 1920×1080). Name it `...-poster.jpg` and store in `01_ASSETS/VIDEO/STILLS/`.

**Video master (used as `animation_url`)**
- **Container:** MP4
- **Codec:** H.264 (AVC), profile High
- **Audio:** AAC (or none). Set `Audio: false` in metadata if silent.
- **Resolution & FPS:** 1080p30 or 4K30 (looping): `1920×1080@30` or `3840×2160@30`
- **Duration:** 6–20 s recommended
- **Looping:** seamless if intended; add `Loop: true` attribute
- **Naming:** `...-4k30-h264-aac-v1.mp4` (master), `...-preview-1080p30.mp4` (light preview)

---

## 3) Collection Chrome (avatars/banners)

Create these once per collection. These are **brand assets**, not item art.

**Collection avatar (square)**
- Export at **800×800 px** (works across OpenSea/Magic Eden/etc.)

**Collection banner / header**
- Export at **1400×400 px** (safe panoramic banner). Keep crucial elements centered.

**Featured/hero image (optional)**
- Export at **1200×600 px** (or 1600×800 px). Use for feature slots when supported.

**Encoding**
- JPG (sRGB), Quality 80–85; PNG if you need transparency or crisp flat graphics.

---

## 4) Preset Matrix by Platform (practical defaults)

| Platform      | Item Preview (sq) | Item Video Poster | Thumb (sq) | Avatar | Banner |
|---------------|-------------------|-------------------|------------|--------|--------|
| OpenSea       | 1600–2048 sq      | 1600 sq           | 512 sq     | 800 sq | 1400×400 |
| Foundation    | 2048 sq (3000 ok) | 1920×1080 or 4K   | 512 sq     | 800 sq | 1400×400 |
| Magic Eden    | 1600 sq           | 1600 sq           | 512 sq     | 800 sq | 1400×400 |
| Objkt (Tezos) | 1600–2048 sq      | 1920×1080 or 4K   | 512 sq     | 800 sq | 1400×400 |
| Rarible       | 1600–2048 sq      | 1920×1080 or 4K   | 512 sq     | 800 sq | 1400×400 |
| Manifold      | 1600–2048 sq      | 1920×1080 or 4K   | 512 sq     | 800 sq | 1400×400 |

> These are **working presets** designed to be safe across UIs. Individual platforms may accept larger sizes/file weights; favor consistency for speed and reliability.

---

## 5) Lightroom / Photoshop Export Tips

**Lightroom Classic (JPG)**
- Resize: Long edge = 1600 (or 2048), **Don’t Enlarge**
- Resolution: 72 ppi (ppi is irrelevant for screens but required by dialog)
- Sharpening: Standard
- File Settings: sRGB, Quality 80–85, Limit File Size if needed (900 KB target for previews)

**Photoshop (Save for Web)**  
- Convert to sRGB, Quality 80–85
- Resize to target px (e.g., 1600), Bicubic Sharper
- Strip metadata (except copyright if desired)

---

## 6) Pipeline Reminders

1. Export **Preview** + **Thumbnail** for every item (and **Poster** for videos).  
2. Store them here:
   - `01_ASSETS/IMAGES/PREVIEWS/…-preview.jpg`
   - `01_ASSETS/IMAGES/THUMBNAILS/…-thumb.jpg`
   - `01_ASSETS/VIDEO/STILLS/…-poster.jpg`
3. Update JSON metadata:
   - `image` → poster (video) or preview (image tokens)
   - `animation_url` → video master (for Relics)
4. Keep previews < 1 MB and thumbs < 120 KB; test loads on mobile.

---

## 7) House Standards (override when needed)

- Default **square** preview: **1600×1600 px** (bump to 2048 for hero pieces).  
- Always export a **square 512×512 thumb**, even for non‑square art.  
- For zoom‑critical works, prepare an extra **3000 px** long‑edge version (watch file size).



---

## 8) Photoshop — Quick Actions (text checklist)

Create 3 actions (Window → Actions). Record each once, reuse forever.

**A. Make PREVIEW (Images)**
1. Convert to Profile: **sRGB IEC61966-2.1**
2. Image Size: **Long edge 1600 px** (or 2048 for heroes), **Bicubic Sharper**
3. Filter → Sharpen → **Smart Sharpen** (Amount 50–80%, Radius 0.3–0.5 px)
4. File → Export → **Save for Web (Legacy)**: JPEG, Quality **80–85**, **Embed Color Profile**
5. Save to: `01_ASSETS/IMAGES/PREVIEWS/…-preview.jpg`

**B. Make THUMBNAIL (Square)**
1. Duplicate current doc (so preview stays open)
2. Canvas Size: **Square crop** around subject if needed
3. Image Size: **512×512 px**
4. Save for Web: JPEG, Quality **75–80** (target **<120 KB**)
5. Save to: `01_ASSETS/IMAGES/THUMBNAILS/…-thumb.jpg`

**C. Make VIDEO POSTER (for Relics)**
1. Open video still or composite frame
2. Convert to sRGB
3. Resize to **1600×1600** (or **1920×1080** for 16:9)
4. Save for Web: JPEG, Quality **80–85**
5. Save to: `01_ASSETS/VIDEO/STILLS/…-poster.jpg`

> Tip: Add a final step in each action to **Close Without Saving** if you’re working from large masters to avoid overwriting.


---

## 9) Lightroom — Export Preset Notes

Create **two export presets** in Lightroom Classic (File → Export → Add):

**Preset 1 — PREVIEW (Square/General)**
- File Settings: **JPEG**, **Quality 80–85**, **sRGB**
- Image Sizing: **Resize to Fit → Long Edge = 1600 px** (or 2048 for heroes), **Don’t Enlarge**
- Output Sharpening: **Screen / Standard**
- Metadata: **Copyright & Contact Info Only**
- File Naming: append `-preview`
- Export To: `01_ASSETS/IMAGES/PREVIEWS`

**Preset 2 — THUMBNAIL (Square)**
- File Settings: JPEG, **Quality 75–80**, sRGB
- Image Sizing: **Width = 512 px**, **Height = 512 px**, **Don’t Enlarge**
- Output Sharpening: **Screen / Standard**
- Metadata: minimal
- File Naming: append `-thumb`
- Export To: `01_ASSETS/IMAGES/THUMBNAILS`

**Optional Preset — VIDEO POSTER**
- Same as PREVIEW but **Long Edge = 1600 px**
- Export To: `01_ASSETS/VIDEO/STILLS`
