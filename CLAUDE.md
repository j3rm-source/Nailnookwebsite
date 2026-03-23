# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file browser game: `tictactoe.html`. Open it directly in any browser — no build step, no dependencies, no server required.

## Architecture

Everything lives in one HTML file with three co-located sections:

- **CSS** (`<style>`) — Dark theme (`#1a1a2e` background). Color palette: red `#e94560` for X, teal `#a8dadc` for O. Grid is 3×3 via CSS Grid, 120px cells.
- **HTML** — Static 9-cell board (`data-i="0"` through `data-i="8"`), score display, status line, restart button.
- **JS** (`<script>`) — All game logic. Key globals: `board` (9-element array), `current` (active player), `over` (game-ended flag), `scores` object `{X, O, T}`. Win detection uses a hardcoded `WINS` array of the 8 possible winning index triplets.

## Git workflow

After every piece of work — no exceptions — stage all changes, commit with a clean descriptive message, and push to `origin master`. Every completed change must exist on GitHub so work is never lost and any state can be reverted.

Commit message format: use a short imperative summary that describes *what changed and why*, e.g. `add AI opponent with minimax`, `fix win detection on diagonal`, `style: darken board background`. Avoid vague messages like "update" or "changes".

A Stop hook in `~/.claude/settings.json` handles this automatically at the end of each session. If making a significant mid-session change (new feature, bug fix), commit explicitly with a meaningful message rather than waiting for the auto-save.
