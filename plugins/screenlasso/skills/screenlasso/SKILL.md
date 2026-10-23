---
name: screenlasso
description: Prepare, resize, crop or convert images with the ScreenLasso app on the user's Mac. Use when the user wants an image for Instagram, Stories, Reels, TikTok, Facebook, X, LinkedIn, Pinterest, a YouTube thumbnail or a link preview, wants WebP or AVIF for a website, or wants to convert an image to WebP, AVIF, JPEG, PNG or HEIC.
---

ScreenLasso runs on the user's Mac and converts images with its `screenlasso` tools. Images stay on the Mac.

1. Call `list_presets` to see the presets and their exact sizes. Prefer a preset whenever the image is for a platform:
   - Instagram feed: `instagram-portrait` (1080 × 1350). Use `instagram-grid` (1080 × 1440) only for posts made in the Instagram app.
   - Stories, Reels and TikTok: `stories` (1080 × 1920).
   - X, LinkedIn, Pinterest, YouTube thumbnails and link previews have their own presets; Facebook keeps the image's shape.
   - A website: `web`, which makes several WebP sizes.
2. For a platform, call `apply_preset` with the preset's id. Social presets crop to the platform's shape from the center, resize to its exact size and convert colors to sRGB, so the platform doesn't rescale the image before its own compression. Tell the user that part of the image is cropped when its shape differs.
3. For anything else, call `convert_image` with a `format` and, if the user wants it smaller, `long_edge` in pixels.
4. Pass the image as `path` when it's in the user's Pictures folder or a folder they allowed in ScreenLasso › Settings › AI Agents. Otherwise pass `image_base64` with a `file_name`. Without `output_folder`, a file given as a path is saved next to it.
5. Reply with where the files were saved and their sizes, as the tool reports them.

If a tool says ScreenLasso isn't reachable or the key isn't accepted, ask the user to open ScreenLasso, turn on **Settings › AI Agents › Let AI agents use ScreenLasso**, and check the key.
