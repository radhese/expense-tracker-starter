# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About this project

Starter project for a Claude Code course on [codewithmosh.com](https://codewithmosh.com/p/claude-code). The app intentionally contains a bug, poor UI, and messy code — fixing these is the point of the course.

## Requirements

Node.js 20.19+ or 22.x is required (Vite 7 dependency). Use nvm to manage versions if needed.

## Commands

```bash
npm run dev      # start dev server at http://localhost:5173
npm run build    # production build
npm run preview  # preview production build
npm run lint     # ESLint (no --fix by default)
```

No test runner is configured.

## Architecture

The entire app lives in a single file: `src/App.jsx`. All state, filtering logic, and rendering are colocated there — no separate components, hooks, or utilities yet. State includes a `transactions` array (with fields `id`, `description`, `amount`, `type`, `category`, `date`) plus form and filter state.

**Known intentional bug:** `amount` is stored as a string (raw input value), so the `reduce` calls for `totalIncome` and `totalExpenses` do string concatenation instead of numeric addition, producing wrong summary totals.
