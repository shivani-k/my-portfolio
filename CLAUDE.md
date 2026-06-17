# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A static single-page HTML portfolio website — no build system, no package manager, no JavaScript framework. Open `index.html` directly in a browser to preview.

## Structure

- `index.html` — the entire portfolio as one page
- `css/style.css` — all styling
- `resources/` — profile photo (`ShivaniKalamadi_PortfolioPic.png`), `favicon.ico`, and `resume.pdf`

## Layout Architecture

Three-column layout (all columns collapse to full-width stacked blocks at ≤1000px):

- **Left panel** (`.left`, fixed, 25% width): profile photo as `background-image` with a teal-blue gradient overlay, name, title (PhD student), institution, and social links (LinkedIn, GitHub, Instagram).
- **Center column** (`.right`, scrollable, 50% width, `margin-left: 25%`): main content sections in order — Introduction, Research Topics, Experience, Education and Projects, resume link, contact form.
- **Right panel** (`.right-panel`, fixed, 25% width): "Recent Highlights" news feed with date-stamped items.

## Section Structure (`.right`)

Each section uses an `h4` heading (`display: block; width: fit-content`) followed by a `.content` block (`display: block; width: 100%`). There is no label/body column split — both stack as full-width blocks.

Key sections and their CSS patterns:
- **Introduction / Research Topics** (`.introduction`): justified `intro-p` paragraphs.
- **Experience** (`.experience`): left-border timeline (`border-left: 2px solid #e8e8e8`), gradient dot `::before` pseudo-element per `.exp-item`. Company, date, role titles with sub-durations.
- **Education and Projects** (`.education`): `.edu-block` per institution with `.edu-header` (university + date flex row), degree, and nested `.edu-projects` (indented, `border-left: 2px solid #f0f0f0`) containing `.project-item` cards.
- **Projects** (`.project-item`): card style (`background: #f9f9fb`, `border-radius: 8px`, subtle shadow), with `.project-title`, `.project-desc`, and optional `.gh-link` button.
- **Resume link**: `<a class="resume">` centered block linking to `./resources/resume.pdf`.
- **Contact form** (`.contact_d`): centered, max-width 480px, POSTs to Formspree.

## External Dependencies (CDN only)

- Google Fonts: Source Sans Pro, Catamaran
- Font Awesome 4.6.3 (icons: `fa-linkedin`, `fa-github`, `fa-instagram`)
- Contact form POSTs to Formspree (`https://formspree.io/f/xvojwybz`) — requires a live internet connection to submit

## Updating Content

All content is hardcoded in `index.html`. To update the resume PDF, replace `resources/resume.pdf`. To add a news item, add a `.news-item` div inside `.right-panel-inner` following the existing date/topic/paragraph pattern — most recent first. Remove stale commented-out blocks rather than accumulating them.
