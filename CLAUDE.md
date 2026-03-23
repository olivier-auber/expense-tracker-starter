# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install       # Install dependencies (required before first run)
npm run dev       # Start dev server at http://localhost:5173
npm run build     # Production build
npm run lint      # Run ESLint
npm run preview   # Preview production build
```

## Architecture

This is a React + Vite single-page expense tracker app. No routing, no global state management.

### Components

- **`App`** — holds the `transactions` array in state (seeded with hardcoded data) and passes it down. Handles adding new transactions via `handleAddTransaction`.
- **`Summary`** — receives `transactions`, computes `totalIncome`, `totalExpenses`, and `balance` internally.
- **`TransactionForm`** — owns its own form state (`description`, `amount`, `type`, `category`). Calls `onAddTransaction(transaction)` on submit, then resets.
- **`TransactionList`** — receives `transactions`, owns filter state (`filterType`, `filterCategory`), and renders the filtered table.

### Key Characteristics

- **No persistence**: state resets on page refresh.
- **Categories**: hardcoded array (`food`, `housing`, `utilities`, `transport`, `entertainment`, `salary`, `other`) duplicated in `TransactionForm` and `TransactionList`.
- **ESLint config**: flat config format; allows unused vars starting with uppercase or `_`.
