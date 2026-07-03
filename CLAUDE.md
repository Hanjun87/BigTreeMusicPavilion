# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**BigTreeMusicPavilion** (大树音乐馆) — a single-page music pavilion site with a retro pixel-art aesthetic.

## Tech Stack

- Plain HTML/CSS/JS — no framework, no build step
- Pixel font: **Zpix** (via jsDelivr CDN), with `PingFang SC` / `Microsoft YaHei` fallback
- Open `index.html` directly in a browser to preview; no server needed

## Layout Architecture

The page uses a **90-degree rotation** pattern:
- `.page` is `100vh × 100vw`, rotated 90° with `transform-origin: center`
- This makes a landscape design fill a portrait screen (intended for vertical displays)
- All positioning inside `.page` is relative to the rotated coordinate system

## Key CSS Conventions

- **Pixel-art look**: `image-rendering: pixelated` on text/buttons; `-webkit-font-smoothing: none` to keep pixel font sharp
- **Pixel box-shadow borders**: buttons and panels use layered `box-shadow` (not `border`) to create a chunky pixel outline with 3D depth — white highlight + dark green shadow
- **Tree-green palette**: `#76a830` (primary green), `#9dd443` (light/hover), `#689831` / `#85b938` (secondary), `#1a3a1a` (dark bg), `#2b572a` (shadow)
- Buttons have `::after` inner border, and `:active` state with `translate(3px, 3px)` for a pressed effect
- Transitions use `steps(2)` for choppy pixel-style animation

## Structure

- **`.btn-group`** — left-side vertical button column: "音乐列表" and "我还想听"
- **`.list-panel`** — music list overlay (7 songs), toggled via JS (`openList`/`closeList`)
- **"我还想听" button** — links to `tencent://message/?uin=2938647756` (QQ chat)
- **`shouye.png`** — homepage background image, displayed via `.bg` with `contain`

## Key Behavior

- Clicking "音乐列表" opens `.list-panel` + `.list-overlay`
- Clicking overlay or ✕ button closes the panel
- No routing, no state management — pure DOM manipulation
