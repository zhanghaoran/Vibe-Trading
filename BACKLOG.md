# Vibe-Trading Backlog

Personal fork customizations and improvements to track.

## Data Sources

### BaoStock A-share Loader
- **Priority:** High
- **Status:** Not started
- **Summary:** Add `baostock_loader.py` as a third fallback for `a_share` market in the loader registry.
- **Why:** AKShare relies on Eastmoney's anti-crawler-protected APIs and frequently hits `ServerDisconnectedError`. Tushare requires a token. BaoStock is free, no registration, highly stable for A-share historical data (daily/weekly/monthly K-line from 1990, 5/15/30/60-min from 1999, financial statements from 2007).
- **Scope:**
  - Create `agent/backtest/loaders/baostock_loader.py`
  - Add `"baostock"` to `_loader_modules` in `registry.py`
  - Insert into `FALLBACK_CHAINS["a_share"]` as `["tushare", "akshare", "baostock"]`
  - Add `baostock` to `pyproject.toml` dependencies
  - Unit tests

### A-share Market Adaptation Rules
- **Priority:** Medium
- **Status:** Not started
- **Summary:** Enforce A-share-specific rules in backtest engine: T+1 settlement delay, daily price limit handling (10%/20% for ST), 100-share minimum lot size.
- **Why:** PVTrade (reference project) has these baked into its strategy base class. Vibe-Trading currently treats A-shares generically.

### SimNow / CTP Futures Simulation
- **Priority:** Low
- **Status:** Not started
- **Summary:** Integrate with SimNow via openctp-ctp for futures paper trading.
- **Why:** PVTrade uses this for live simulation. Bridges the gap between backtest and real execution.

## Risk Management

### A-share Specific Risk Rules
- **Priority:** Medium
- **Status:** Not started
- **Summary:** Implement configurable risk constraints: per-trade risk (e.g. 1% equity via ATR position sizing), per-symbol cap, per-industry cap, portfolio heat limit.
- **Why:** PVTrade enforces 1% per-trade / 5% per-symbol / 25% per-industry / 15% heat. Vibe-Trading's risk tools are general-purpose.

---

*Last updated: 2026-05-02*
