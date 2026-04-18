# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository

GitHub: https://github.com/flamingfalcon33-create/claude-code-stuff

**Git workflow — required on every task:**
- Commit and push to `origin main` after every meaningful unit of work (feature added, bug fixed, file created).
- Never leave completed work uncommitted — each push is a save point we can revert to.
- Commit messages must be clean and descriptive: imperative mood, short subject line (e.g. `Add AI opponent to tictactoe`), no filler.
- Stage files specifically by name rather than `git add .`.

## Project Structure

This is a single-file web project. Each game or tool lives as a standalone `.html` file with all CSS and JS inlined — no build step, no dependencies, no package manager.

To run any file, open it directly in a browser.

## Current Files

- `tictactoe.html` — Two-player Tic Tac Toe with score tracking, win highlighting, and a dark theme.

## Architecture: tictactoe.html

- **State**: `board` (9-element array), `current` (active player `'X'`/`'O'`), `over` (boolean), `scores` object persisted across games.
- **Win detection**: `checkWinner()` iterates the 8 `WINS` combos; returns `{ winner, line }` on win or `{ winner: null, tie: true }` on draw.
- **DOM**: 9 `.cell` divs addressed by `data-i` index. Classes `taken`, `x`/`o`, and `win` drive all visual state.
- **Reset**: `init()` resets board/state and clears cell classes/text without touching `scores`.
