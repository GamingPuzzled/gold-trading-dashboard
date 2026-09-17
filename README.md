# Gold Trading Dashboard

Live view of paper-trading portfolios across Kalshi's 15-minute markets, running
the "extreme-favorite" strategy (buy the side that's become an overwhelming
favorite, threshold 0.85). Strategy code and backtests:
https://github.com/GamingPuzzled/gold-trading (private).

**Gold and Copper** run as real live_trading bots -- own bankroll, own
strategy_stats, actually executing paper orders via `orchestration/scheduler.py`.

**Everything else** (BTC, ETH, XRP, Silver, WTI, Solana, Dogecoin,
Hyperliquid, Zcash, BNB, NEAR, Natural Gas) is marked "simulated" on the
dashboard: paper-simulated from a passive orderbook watcher
(`backtest/live_crossing_watcher.py`) that logs real 5-second order-book
snapshots without trading, fed through the same detection logic
(`backtest/live_paper_simulator.py`) at a fixed 10-contract size. No live
bot runs behind these yet -- they exist to accumulate evidence on markets
gold/copper's own backtests didn't clearly support before committing a real
bot to them.

`data.json` is regenerated every 5 minutes (`dashboard-export.timer`) and
pushed here automatically. Paper trading only — no real money is involved.
