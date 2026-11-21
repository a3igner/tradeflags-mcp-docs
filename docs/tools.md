# TradeFlags MCP — tools

35 tools across 27 packages.

Every tool is read-only and returns an `as_of` timestamp.

## accumulator-prices
- **accumulator__history** — Live indicative accumulator quotes: spot, accrual level, knockout barrier and modelled knockout probability for each stock, variant and leverage, for the stated session.
- **accumulator__price** — Price a single accumulator on demand: given a stock, variant, leverage and optional anchor, return the solved structure with NPV and Greeks. Computed live.

## ads-index
- **ads__index** — The Aruoba-Diebold-Scotti Business Conditions index: real-time daily tracking of US economic conditions, with a regime reading.

## cranex
- **cranex__sentiment** — A composite sentiment dial over five assets (S&P 500, Nasdaq, crude oil, Bitcoin, Ethereum), with each asset's score, 24-hour regime and volatility.

## crypto-trend-signals
- **crypto_trend__state** — Live trend state for a crypto pair on 1-minute bars: parabolic-SAR level, ATR-normalised distance to a flip, and the risk multiple of the open leg.

## golden-death-cross
- **golden_death_cross__series** — Net golden minus death crosses across the HK universe, with the 100-day trend band and the latest per-stock cross signals.

## hilo
- **hilo__series** — The HK Hi-Lo breadth oscillator: percentage of advancing vs declining issues, with its 100-day band and regime state.

## hindenburg-omen
- **hindenburg__series** — The Hindenburg Omen breadth reading: new highs/lows, the McClellan oscillator condition, and whether the omen fired and confirmed, per trading day.

## hk-rasi
- **hk_rasi__series** — The Ratio-Adjusted Summation Index: breadth normalised to 1000 issues so readings stay comparable across listing changes.

## hk-trin
- **hk_trin__series** — Both Arms Index variants: $TRIN (dollar-weighted) and TRIN (share-weighted), each with its 100-day band.
- **hk_trin__scatter** — The HSI/$TRIN scatter: each day's dollar-weighted $TRIN against the HSI daily percentage change, with the latest 100-day band, the VHSI daily-vol bound, and realised-volatility readouts.

## hkma-curve
- **hkma__curve** — The HKMA HKD interest-rate curve: par and zero yields by tenor, as published by the Hong Kong Monetary Authority.

## hsi75-term-structure
- **hsi75__term_structure** — The HSI75 term-structure ratio: synthetic 3M vs 1M implied volatility built from constituent options, correlation-adjusted and cross-checked against VHSI, with coverage status.

## mcclellan
- **mcclellan__series** — The McClellan Summation Index: the cumulative trend of the breadth oscillator, with a 100-day trend band.

## moirai-forecaster
- **moirai__forecast** — Moirai distribution forecasts for the Hong Kong market: P10, median and P90 over one-day and thirty-day horizons, with confidence and the probability of an up move.

## network-of-companies
- **network__nodes** — The supply-chain network node set: each company with its centrality and bottleneck scores.
- **network__edges** — The weighted relationships between companies: type, dependency level and revenue exposure.
- **network__valuation** — Peer-relative valuation: z-scores of the key multiples against the peer group, the composite and network-adjusted signal, and average correlation.
- **network__scenarios** — The what-if shock scenarios with the reach and revenue-at-risk of each.

## news-sentiment
- **news__sentiment** — Headline-level sentiment on scored market news: a polarity reading with a negative/neutral/positive split, tagged by topic.

## otc-pricing
- **otc_pricing__price** — Price an over-the-counter HK retail equity derivative from its structure parameters (strike, barrier, base level, leverage, volatility) using the Monte Carlo engine, returning net present value and Greeks. Computed on demand.

## power-ratio
- **power_ratio__signals** — Aigner & Schrabmair's Power Ratio: normalised signal and noise power over six trailing windows (10..200 days), each a multiple of the stop-loss range, with the volatility trigger.

## sar-signals
- **sar__signals** — Parabolic SAR trend reversals across the HK market: flip direction, the new SAR stop level, the ATR it was measured against, and the full SAR series per stock.

## signal-outcomes
- **signal_outcomes__results** — Signal-to-outcome results: for each fired signal, the forward return, max drawdown and whether it hit, by source and horizon.

## skew-25d
- **skew_25d__series** — The 25-delta put-minus-call skew for HSI by contract month, with the z-score against its own history and the regime it implies.

## td-sequential
- **td_sequential__signals** — Tom DeMark sequential buy/sell setups across the HK market: direction, signal type, setup phase, qualifier/perfection counts and TDST levels, with traded size. Includes buy-setup and exhaustion variants.

## tfx-index
- **tfx__composite** — The HK cross-asset risk composite over volatility, credit and FX, with a z-score and a market-phase band.

## universe-indicators
- **universe_indicators__daily** — The per-stock universal indicator: a daily composite across the signal sources, with the source count and weights used, across the full HK universe.

## vix-vhsi
- **vix_vhsi__levels** — The two headline volatility gauges side by side: CBOE VIX for US equities and HKEX VHSI for the HSI, with daily change and regime.

## vix-vix3m
- **vix_vix3m__ratio** — The VIX against VIX3M ratio with its component readings, near/medium VIX futures and front-month contango, per trading day.

## vol-surface
- **vol_surface__term_structure** — HSI implied-volatility term structure: ATM volatility, 25-delta put-minus-call skew and convexity per contract month, in volatility points, for the stated snapshot session.
- **vol_surface__surface** — One-dimensional slice of the HSI fitted implied-volatility surface: give an expiry to get the smile (IV vs strike), or a strike/moneyness to get the term (IV vs expiry). Fitted values only. One slice per call.

## vol-surface-hk
- **vol_surface_hk__term_structure** — Per-stock implied-volatility term structure for a Hong Kong equity: ATM volatility and 25-delta skew per expiry, fitted, in volatility points.
- **vol_surface_hk__surface** — One-dimensional slice of a single Hong Kong stock's fitted implied-volatility surface: an expiry returns the smile (IV vs strike); a strike returns the term (IV vs expiry). Fitted values only.
- **vol_surface_hk__spot** — Current spot and days-to-expiry for the optionable Hong Kong equities, as of the latest snapshot session.
