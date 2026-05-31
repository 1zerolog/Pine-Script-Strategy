# Pine Script Strategy Template

A reusable strategy template for TradingView Pine Script v6.

This repository provides a base Pine Script structure for building new trading strategies. The long and short entry conditions are intentionally left blank, so you can add your own trend logic, signal rules, filters, or indicator-based conditions inside the `TREND-STRATEGY`, `MAIN-STRATEGY`, and `FINAL_CONDITIONS` sections.

## Files

- `Template/Template.pine`: TradingView Pine Script v6 strategy file.
- `Template/Template.txt`: Text/reference copy of the same strategy.

## Features

- Pine Script v6 strategy structure
- Toggleable long and short entries
- Backtest date range filter
- Position sizing based on leverage and equity percentage
- Separate alert/comment IDs for long and short entries/exits
- Take-profit and stop-loss logic based on average position price
- One-time market close logic for TP/SL triggers
- Trailing stop close system for long and short positions
- State reset logic for pyramiding or position size changes

## Usage

1. Copy `Template/Template.pine` into the TradingView Pine Editor.
2. Add your indicators or signal logic inside the `TREND-STRATEGY` and `MAIN-STRATEGY` sections.
3. Define the `enterLong` and `enterShort` conditions in the `FINAL_CONDITIONS` section.
4. Adjust the backtest, leverage, TP/SL, and trailing stop settings from the TradingView input panel.

Example final condition structure:

```pine
enterLong  = longSignal and trendUp
enterShort = shortSignal and trendDown
```

## Main Settings

| Setting | Description |
| --- | --- |
| `Backtest` | Enables or disables the date range filter. |
| `Start` / `End` | Defines the backtest date range. |
| `Enter Long Position` | Enables long entries. |
| `Enter Short Position` | Enables short entries. |
| `LEVERAGE (%)` | Defines the percentage of equity to use. |
| `LEVERAGE (X)` | Leverage multiplier used in position size calculation. |
| `TP %` | Take-profit percentage based on the average position price. |
| `SL %` | Stop-loss percentage based on the average position price. Set to `0` to disable SL. |
| `Trail Point %` | Price distance required to activate the trailing stop. |
| `Trail Offset %` | Follow distance after the trailing stop becomes active. |

## Notes

- This file is a starting template for strategy development, not a complete ready-to-trade strategy.
- Pine Editor may show an error until `enterLong` and `enterShort` are properly defined.
- Default commission is `0.1%`, initial capital is `100 USD`, and position sizing is based on equity percentage.
- Before using it in live markets, test it across different symbols, timeframes, and market conditions.

## Disclaimer

This repository is not financial advice. The strategy template is shared for educational, testing, and development purposes only. Before using it in live trading, always consider risk management, slippage, commissions, and market conditions.
