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

This is a React + Vite single-page expense tracker app. The entire application lives in a single component: **`src/App.jsx`**.

### State & Data Flow

All state is managed with `useState` hooks directly in `App.jsx` — no global state, no context, no routing:

- `transactions` — array of transaction objects `{ id, description, amount, type, category, date }`
- Form state: `description`, `amount`, `type`, `category`
- Filter state: `filterType`, `filterCategory`

Derived values (`totalIncome`, `totalExpenses`, `balance`, `filteredTransactions`) are computed inline from state on each render.

Transactions are seeded with hardcoded sample data on mount. There is no persistence — state resets on page refresh.

### Key Characteristics

- **Monolithic component**: No component decomposition — the form, summary cards, and transaction table are all rendered from `App.jsx`.
- **No routing**: Single view only.
- **Categories**: Hardcoded array (`food`, `housing`, `utilities`, `transport`, `entertainment`, `salary`, `other`).
- **ESLint config**: Flat config format; allows unused vars starting with uppercase or `_`.
