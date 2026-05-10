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

`App.jsx` is the root — it owns the `transactions` array (fields: `id`, `description`, `amount`, `type`, `category`, `date`) and a `handleAdd` callback, then delegates everything else to three child components:

- **`Summary.jsx`** — receives `transactions`, computes `totalIncome`, `totalExpenses`, and `balance` internally, renders the three summary cards.
- **`TransactionForm.jsx`** — owns its own form state (`description`, `amount`, `type`, `category`), calls `onAdd(transaction)` on submit. Receives `categories` as a prop.
- **`TransactionList.jsx`** — owns its own filter state (`filterType`, `filterCategory`), renders the filtered table. Receives `transactions` and `categories` as props.

`categories` is a module-level constant in `App.jsx`, passed down to both `TransactionForm` and `TransactionList`. Transaction `amount` is always stored as a number (`parseFloat`).
