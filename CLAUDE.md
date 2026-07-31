# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static personal/business website for Claes Svensson IT AB. It can be served via GitHub Pages (repo `wwwclaes.github.io`, custom domain `claessvensson.com` set via `CNAME`), but is currently served using another hosting service. There is no build step, no package manager, and no test suite — the site is plain HTML/CSS/JS served as-is.

## Working with this repo

- `index.html` is the entire site content. Edit it directly.
- `assets/css`, `assets/js`, `assets/fonts` are vendored third-party libraries (Bootstrap, ionicons, jQuery, retina.js) — treat them as read-only unless upgrading a dependency intentionally.
- `assets/img` holds site images.
- `cv.pdf` is linked directly from the page (`/cv.pdf`) and served at the site root.
- There is no local dev server, bundler, or preprocessor. To preview changes, open `index.html` directly in a browser or serve the directory with any static file server (e.g. `python3 -m http.server`).
- Deployment is implicit: pushing to the repo's default branch updates the live GitHub Pages site (`claessvensson.com`) — there is no separate build/deploy pipeline.

## Notable implementation detail

The footer email and phone number are rendered via inline "email obfuscator" `<script>` blocks (a substitution-cipher decoder) rather than plain text, to deter scraping. If editing contact info, regenerate the obfuscated string rather than hardcoding plaintext into the HTML.
