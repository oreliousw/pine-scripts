# 🧠 Mr O’s Pine Script Build / Debug Template
**Purpose:** Standard workflow and AI prompt structure for creating, debugging, and versioning TradingView Pine Scripts compatible with your OANDA Bridge JSON alert format.

---

## 🎯 Overview

Use this template when starting any new Pine Script project or version.  
It keeps alert formatting, variable naming, and sectioning consistent across all builds.

---

## 🧩 Add-On Prompts

| Purpose | Mini-Prompt |
|----------|-------------|
| 🔍 Fix compile error | “Here’s the TradingView compile error: [paste error]. Fix only the cause — don’t change the JSON alert format.” |
| 🧩 Add new feature | “Add [feature] as optional input — disabled by default. Keep alert logic intact.” |
| 🧮 Tune parameters | “Explain how changing RSI length from 14 → 7 affects signal frequency under current filters.” |
| 🧱 Merge versions | “Merge PSv3.36 and PSv3.4e keeping best logic from each. Keep alert JSON identical.” |
| 🧾 Create changelog | “Generate a CHANGELOG.md entry for this Pine update (same format as my TVCHANGELOG).” |

---

## 🔁 Bonus Flow

1. Paste your current script.  
2. Ask GPT-5: *“Fix compile errors and label each section clearly.”*  
3. Once it compiles, say: *“Okay, now enable new RSI-based reversal filter, optional input.”*  
4. Save as `PSvX.Y` and log it in your changelog.  
5. Continue incremental updates: small blocks → compile → test → document.

*(yukkuri daijoubu = “take it slow, it’s okay”) 💪*
                          
You are a Pine Script co-pilot helping Orelious (“Mr O”) build and debug the TradingView indicator series used with the OANDA Bridge.

📦 Project
- Script name: PSv4.3 – Direction + JSON Alerts  
- Base version: PSv3.3 stable  
- Integration: OANDA Bridge via JSON webhooks  
- Style: Momentum (multi-TF RSI + SMA trend filter)  
- Requirements: ATR-based SL/TP, JSON alerts for BUY/SELL/TP/SL  

🧠 Rules Output format
- Full commented Pine Script v6 (one block, ready for TradingView)
- Sectioned comments for each logic block   
- Short summary of what was added/changed  
- If you detect syntax issues, fix inline before posting
- Keep all alert JSON sections exactly as-is (same structure/format for your OANDA bridge)
- Do not rename or remove JSON keys.
- Use clear, labeled sections
- If compile error occurs, fix it — no redesigns or breaking JSON
---


## 🧭 Next Step

To start your next script:
1. Copy the Example Prompt above.  
2. Paste it into GPT-5.  
3. Replace the project name, base version, and goal.  
4. Watch it build a clean, structured Pine Script ready for TradingView.

---

*Maintained by Orelious (“Mr O”) – CFII ✈️ • Momentum Trader 📈 • Exec Flight Services Founder*
