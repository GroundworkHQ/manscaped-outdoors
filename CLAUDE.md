# manscaped-outdoors — Claude Code context

## Read first
Before working, read **`docs/REFERENCE.md`** — the source of truth for this project. This file is just the quick orientation.

## What this is
Landing/sales page redesign for Manscaped Outdoors, a landscaping company in Clarkesville, GA. Current site (manscapedoutdoors.com) is outdated and being replaced. Frontend-only for now — CRM, AI chatbot, and AI inbound call/text agent are planned future phases, not in current scope.

## Stack
Simple static HTML/CSS/JS. Deployed via GitHub Pages.

## Conventions & rules
- Secrets live in env vars / `.env.local` only, never in code. `.env.local` is gitignored. Rotate immediately if exposed.
- Commit + push at the end of each session to back up. Commit messages end with the Co-Authored-By line.
- Reference assets/briefs live in the client's Google Drive folder ("Manscaped Outdoors") — check there before asking the client for materials that may already exist.

## Current priority
Build the frontend landing/sales page to replace the current live site.

Immediate next step: search Envato Elements for a hero-section background video (drone/landscaping footage). This was deferred to a fresh session because no Envato MCP was connected — check for one before falling back to browsing elements.envato.com manually via the Chrome extension.
