---
name: screenlasso
description: Edit, mark up, resize, crop or convert images, read text, work with colors and QR codes, and convert videos with the ScreenLasso app on the user's Mac. Use when the user wants an image for Instagram, Stories, Reels, TikTok, Facebook, X, LinkedIn, Pinterest, a YouTube thumbnail or a link preview; wants WebP or AVIF for a website; wants to resize, crop, watermark, add a logo or border, adjust colors, remove the background or hide faces and text; wants arrows, boxes, text or numbered steps drawn on a screenshot; wants a color converted (HEX, RGB, HSL, OKLCH, Tailwind, SwiftUI…), its contrast checked or a palette; wants the text in an image or on screen read (OCR); wants a QR code read; wants a video or GIF converted; or wants a folder of images converted.
---

ScreenLasso runs on the user's Mac. Its `screenlasso` tools work on files there, and images stay on the Mac.

## Images

- **For a platform**, call `list_presets`, then `apply_preset`. Social presets crop to the platform's shape from the center, resize to its exact size and convert to sRGB, so the platform doesn't rescale before its own compression:
  - Instagram feed: `instagram-portrait` (1080 × 1350); `instagram-grid` (1080 × 1440) only for posts made in the Instagram app.
  - Stories, Reels and TikTok: `stories` (1080 × 1920). X, LinkedIn, Pinterest, YouTube thumbnails and link previews have their own; Facebook keeps the shape.
  - A website: `web`, which makes several WebP sizes.
  Tell the user when part of the image is cropped.
- **Another format or size**: `convert_image` with `format` and, to make it smaller, `long_edge`.
- **Edits**: `edit_image` with an `edits` list, applied in order — resize, crop, trim_borders, add_canvas, rotate, watermark, logo, border, round_corners, fill_transparency, auto_enhance, adjust, color_effect, sharpen, reduce_noise, blur, remove_background, hide_faces_text, srgb, metadata. Choose `format` (png by default).
- **Marking up**: `annotate_image` with `marks` in image pixels from the top left — arrow, line, rectangle, highlight, text, number (numbered steps), pixelate, pen. Read the image first to place marks where they belong; keep text short and choose a color that stands out from the background.
- **A whole folder**: `batch_convert` with a `preset` or a `format`; results go into an `Optimized` subfolder.

Pass an image as `path` when it's in the Pictures folder or a folder allowed in ScreenLasso › Settings › AI Agents; otherwise as `image_base64` with a `file_name`. A file given as a path is saved next to it unless `output_folder` says otherwise. Files are never replaced.

## Colors

`convert_color` gives HEX, RGB, HSL, HSB, CMYK, OKLCH and the nearest Tailwind class (`all_formats` adds code for SwiftUI, NSColor, UIColor, Android, Java and .NET). `check_contrast` gives the WCAG ratio and, when it fails, the closest text colors that pass. `color_harmony` finds matching colors, `extract_palette` an image's main colors, and `save_palette` keeps colors in ScreenLasso's color picker.

## Text, QR codes and videos

`read_text` reads the text in an image on the Mac (OCR), Turkish and English included, in reading order. Pass `include_lines` for each line with its position, and `languages` (e.g. `["tr", "en"]`) when the language is known. For text on the user's screen, ask with `capture_screen` first, then pass the image.

`read_qr` reads QR codes in an image, including Wi-Fi networks. `convert_video` turns a video or animated GIF/WebP into a web or sharing MP4, an archive copy, or a GIF or animated WebP.

## The screen

`capture_screen` asks the user to capture an area (`mode: area`, the default), the screen (`full_screen`), the window they click (`window`) or a long page they scroll (`scrolling`, joined into one tall image). `record_screen` asks them to record an area or the screen, without sound, until they stop or `max_seconds` (at most 120) pass, and returns the movie's path; `convert_video` makes it an MP4 or a GIF. `pick_screen_color` asks them to pick a color. These work only when the user turned on **Allow screen capture** in ScreenLasso's settings. ScreenLasso asks the user every time; give a short `reason`. If the user declines, don't ask again unless they want to.

## Answering

Reply with where files were saved and their sizes, as the tools report them. If a tool says ScreenLasso isn't reachable or the key isn't accepted, ask the user to open ScreenLasso, turn on **Settings › AI Agents › Let AI agents use ScreenLasso**, and check the key.
