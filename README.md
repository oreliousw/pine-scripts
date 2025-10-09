# PSv4.3-ChatGpt (Adaptive RR + Alert Spacing + Slim Core)

### 📘 Overview

**PSv4.3-ChatGpt** is the latest streamlined generation of your Pine Script momentum system.
It merges the proven multi-timeframe RSI/Trend logic from v3.3–v4.1 with:

* Adaptive RR management (tightens targets in high volatility)
* Smart alert spacing (prevents noise spam)
* Optional strict trend alignment (All 3 TFs vs 2-of-3)
* Cleaned, minimal core—no dock overlay—for faster runtime

The script remains fully compatible with **OANDA Bridge JSON alerts**.

---

### ⚙️ Installation

1. Open **TradingView → Pine Editor**.
2. Paste the full script and **Add to Chart**.
3. Save as **PSv4.3-ChatGpt**.
4. Configure Inputs → Enable “Buy/Sell” alerts → Select **“Once per bar close.”**

---

### 🥉 Parameter Overview (Condensed)

| Category          | Parameter                    | Description                            | Default  |
| ----------------- | ---------------------------- | -------------------------------------- | -------- |
| **Core**          | `rsiLength`                  | RSI period                             | 14       |
|                   | `maLength`                   | SMA trend length                       | 50       |
|                   | `emaLength`                  | EMA trend length                       | 20       |
| **Flex/Reversal** | `useFlexMode`                | Enables RSI cross reversal logic       | ✅        |
|                   | `rsiOffset`                  | RSI offset for reversal range          | 5        |
|                   | `rsiBuyLevel / rsiSellLevel` | RSI thresholds                         | 60 / 40  |
| **Trend Filter**  | `useTrendFilter`             | Activates TF alignment                 | ✅        |
|                   | `trendMode`                  | “Strict (All 3)” or “2-of-3” alignment | “2-of-3” |
| **ATR / Stops**   | `atrLen`                     | ATR period                             | 14       |
|                   | `atrMult`                    | SL distance multiplier                 | 1.5      |
|                   | `rr`                         | TP risk / reward ratio                 | 2.0      |
|                   | `minSlPips`                  | Minimum stop distance                  | 2.0      |
| **Adaptive RR**   | `useAdaptiveRR`              | Tightens RR on high ATR volatility     | ✅        |
|                   | `volAtrMult`                 | High-vol threshold = ATR × this        | 2.0      |
|                   | `rrTightFactor`              | TP tighten ratio (0.25–1.0)            | 0.75     |
| **Trailing Stop** | `useTrailing`                | Enables ATR trailing SL                | ❌        |
|                   | `trailActivate`              | RR level to activate trailing          | 0.5      |
| **Filters**       | `useCoreFilters`             | Volume / MACD / SR / Engulfing         | ✅        |
|                   | `maxDriftPips`               | Max pips change per bar to allow       | 5.0      |
|                   | `useBBFilter`                | Require BB zone alignment              | ✅        |
| **Sessions**      | `useSession`                 | Limit to London + NY (08–22 GMT)       | ✅        |
| **Alert Control** | `useAlertThreshold`          | Enforce min pips between alerts        | ✅        |
|                   | `alertFilterThreshold`       | Min move between alerts (pips)         | 10       |
| **Auto Reset**    | `autoClear`                  | Clears trade vars after TP/SL          | ✅        |

---

### 🚀 Alert JSON Format (for OANDA Bridge)

```json
{
  "message": "BUY",
  "entry": 1.08645,
  "sl": 1.08490,
  "tp": 1.08945,
  "instrument": "EUR_USD",
  "timestamp": "2025-10-08 15:45:00",
  "risk_pips": 15.5
}
```

TP / SL alerts also emit:

```json
{"message":"TP","instrument":"EUR_USD","timestamp":"2025-10-08 15:45:00","est_pnl_pips":22.3}
```

---

### 🧠 System Highlights

* **Adaptive Risk Reward Engine** → Dynamic RR tightening under volatility.
* **Smart Alert Spacing** → Pip-based distance filter for clean signal streams.
* **Symmetrical Trend Logic** → Balanced 2-of-3 alignment for both directions.
* **ATR Guard & Trailing** → Volatility-aware stop logic.
* **Lightweight Core** → No dock, faster execution for multi-chart setups.

---

### 📞 Changelog (v3.3 → v4.3)

| Version         | Major Changes                                                            |
| --------------- | ------------------------------------------------------------------------ |
| **v3.3**        | Base dock panel + JSON alerts                                            |
| **v3.4 – v3.7** | ATR SL/TP logic + OANDA sync                                             |
| **v3.9**        | Bollinger + Reversal structure                                           |
| **v4.0**        | Unified reversal engine (EMA option)                                     |
| **v4.1**        | ATR Guard + Active Trade Lock                                            |
| **v4.2**        | Slim rewrite + clean alert structure                                     |
| **v4.3**        | ✫ Adaptive RR · Alert Spacing · Symmetrical Trend Filter · Timestamp fix |

---

### ⚙️ **Core Tuning Guide**

| Category            | Setting                  | Typical Range                                                        | Effect on Trade Frequency / Quality |
| ------------------- | ------------------------ | -------------------------------------------------------------------- | ----------------------------------- |
| **RSI Sensitivity** | `rsiLength` 7–16         | Lower = faster signals (more noise). Higher = cleaner fewer signals. |                                     |
| **Trend Strength**  | `maLength` 20–50         | Shorter = quicker 5M entries; longer = smoother.                     |                                     |
| **Trend Mode**      | `Strict (3)` vs `2-of-3` | Strict = strong confirmation, fewer signals.                         |                                     |
| **Flex Reversal**   | `rsiOffset` 3–8          | Wider offset = more reversal catch potential.                        |                                     |
| **ATR Multiplier**  | 1.0 – 2.5                | Wider stops reduce whips; tighter increase frequency.                |                                     |
| **Risk Reward**     | 1.5 – 3.0                | Higher RR = fewer TPs, larger wins.                                  |                                     |
| **Adaptive RR**     | `rrTightFactor 0.75`     | Tightens TP when ATR > 2× avgATR.                                    |                                     |
| **Trailing Stop**   | `trailActivate 0.5`      | Activates after halfway to target.                                   |                                     |
| **Core Filters**    | toggle                   | Disable for testing pure trend.                                      |                                     |
| **Alert Spacing**   | 5 – 15 pips              | Raise to reduce noise; lower for faster reactivity.                  |                                     |

#### 🎯 Suggested Profiles

| Style            | Example Settings                                                 | Behavior                                |
| ---------------- | ---------------------------------------------------------------- | --------------------------------------- |
| **Scalper**      | RSI 7 · MA 20 · `2-of-3` · ATR 1.2 · RR 1.5 · Alert 5 pips       | High frequency signals, tight targets.  |
| **Swing**        | RSI 14 · MA 50 · `2-of-3` · ATR 1.5 · RR 2.0 · Alert 10 pips     | Balanced mix of frequency and accuracy. |
| **Trend Holder** | RSI 16 · MA 50 · `Strict (3)` · ATR 2.0 · RR 2.5 · Alert 15 pips | Conservative entries, longer holds.     |

---

### 🤖 Before Live Run Checklist

* ✅ Verify OANDA webhook URL in alert settings.
* ✅ Match timeframes (4H/1H/5M) in inputs.
* ✅ Enable `useAlertThreshold` to prevent duplicate signals.
* ✅ Check for “BUY” / “SELL” alerts firing with valid JSON fields.

---

**Author:** Orelious (“Mr O”)
**License:** MPL 2.0
**Repo:** [`oreliousw/pine-scripts`](https://github.com/oreliousw/pine-scripts)

---

*“Yukkuri daijōbu” — take it slow, it’s okay ✈️*

### 📞 Changelog (v3.3 → v4.3)

| Version  | Major Changes          |
| -------- | ---------------------- |
| **v3.3** | Base dock panel + JSON |
