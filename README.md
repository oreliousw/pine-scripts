[psv_4.md](https://github.com/user-attachments/files/22785630/psv_4.md)
# PSv4.1 (ATR Guarded + Active Trade Lock)

### 📘 Overview
**PSv4.1** represents the most advanced iteration of your momentum‑based Pine Script system. It combines the multi‑timeframe RSI structure from v3.3 with an *Active Trade Lock* system, ATR‑guarded SL/TP logic, reversal detection, and dynamic RR management. The script is compatible with TradingView alerts formatted for OANDA bridge automation.

---

### 🧩 Installation
1. **Open TradingView → Pine Editor.**  
2. Paste the full script from this repository into a new indicator.  
3. Click **Add to chart** → **Save as PSv4.1**.  
4. Configure your parameters in the Inputs tab.  
5. Enable alerts using the “Buy/Sell” alert JSON outputs for webhook delivery.

---

### ⚙️ Parameter Overview (Condensed)
| Category | Parameter | Description | Default |
|-----------|------------|--------------|----------|
| **Core** | `rsiLength` | RSI period | 14 |
| | `maLength` | SMA trend filter length | 50 |
| | `emaLength` | EMA trend length | 20 |
| **Reversal** | `useReversalMode` | Enables reversal logic using RSI & BB crosses | ✅ |
| | `rsiReversalOffset` | RSI offset for reversal cross | 8 |
| **ATR/Stops** | `atrLen` | ATR period | 14 |
| | `atrMult` | ATR multiplier for SL | 1.5 |
| | `rr` | TP risk‑reward ratio | 2.0 |
| | `minSlPips` | Minimum stop distance | 2.0 |
| **Trade Management** | `useTrailing` | Enables ATR trailing stop | ❌ |
| | `trailActivate` | RR level to start trailing | 0.5 |
| | `autoClear` | Reset trade vars after TP/SL | ✅ |
| **Filters** | `useVolumeFilter`, `useMACDFilter`, `useSRFilter`, `useCandleFilter`, `useBBFilter` | Layered confirmations | ✅ |
| **Sessions** | `useSessionFilter` | Restrict to London/NY sessions | ✅ |
| **Dynamic RR** | `useDynamicRR` | Tightens RR under high volatility | ✅ |

---

### 🚀 Alert JSON (for OANDA Bridge)
Each new trade alert fires once per bar close and includes full trade metadata.
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

---

### 🧠 System Features Summary
- **Active Trade Lock** → prevents overlapping trades until SL/TP resolution.  
- **ATR Guard** → filters micro‑range setups; ignores low‑ATR noise.  
- **Reversal Detection** → dual RSI/BB confirmation for early reversals.  
- **Dynamic Risk‑Reward** → adapts TP distance under volatility spikes.  
- **Multi‑TF RSI Trend Alignment** → 4H / 1H / 5M agreement triggers.  
- **Dock Panel Display** → live TF trends, RSI, RR, and PnL snapshot.  

---

### 🧾 Changelog Summary (v3.3 → v4.1)
- **v3.3** → Core dock + JSON alerts foundation.  
- **v3.4–v3.7** → ATR SL/TP, OANDA sync, error handling.  
- **v3.9** → Bollinger + RSI reversal groundwork.  
- **v4.0** → Reversal filter integration, syntax refinements.  
- **v4.1** → Active Trade Lock, ATR Guard, precomputed swing fixes, stable compile.

---

### 🪄 Tips
- Set `rr = 1.5` and `atrMult = 2.0` for tighter, reversal‑friendly trades.  
- For slower pairs (e.g., EUR/CHF), reduce `rsiLength` to 7–10.  
- For volatile pairs (e.g., GBP/JPY), use `useDynamicRR = true` with `volAtrMult = 2.5`.  
- Keep alerts restricted to 5M timeframe; higher TFs act as trend filters.

---

**Author:** Orelious  
**License:** Mozilla Public License 2.0  
**Repo:** [`oreliousw/pine-scripts`](https://github.com/oreliousw/pine-scripts)

---

_“Yukkuri daijoubu” — take it slow, it’s okay. ✈️_

