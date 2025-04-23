# 🤖 AI Crypto Trading Bot

This is a fully autonomous, self-learning crypto trading bot that uses machine learning, technical indicators, and real-time market data to simulate (and optionally execute) trades on Binance.

---

## 🚀 Features

- ✅ **Self-Learning Loop**: Bot retrains itself hourly based on past trade outcomes.
- 📈 **Live Market Simulation**: Trades simulated every 10 seconds using live Binance data.
- 🤖 **AI Model**: XGBoost classifier trained on RSI, EMA, MACD, and Bollinger Bands.
- 📰 **News Sentiment**: Adjusts confidence using recent crypto news headlines from CryptoPanic.
- 📉 **Dynamic SL/TP**: Calculates take-profit and stop-loss levels per trade based on market volatility and model confidence.
- 🔁 **Symbol Selector**: Choose BTC/USDT, ETH/USDT, or SOL/USDT at startup.
- 📝 **Trade Logging**: All trades are logged to `simulated_trade_log.csv` with full trade stats.

---

## 🧠 How It Works

1. **Initial Training**: On first run, it loads ~2 months of historical trades and trains an XGBoost model.
2. **Signal Generation**: Every 10s, the model predicts whether to go long, short, or stay out.
3. **Trade Simulation**: If confidence is high, it simulates a trade with live price monitoring until TP or SL is hit.
4. **Self-Learning**: After each hour, the model is retrained using its own logged trade outcomes.

---

## 📦 Installation

```bash
git clone https://github.com/your-username/ai-trading-bot
cd ai-trading-bot
pip install -r requirements.txt
```

### Dependencies
- `ccxt`
- `pandas`
- `ta` (technical analysis library)
- `xgboost`
- `scikit-learn`
- `requests`

---

## ▶️ Running the Bot

```bash
python main.py
```

You'll be prompted to select a trading symbol. The bot will start trading live market data with simulated trades.

---

## ⚙️ Settings

Edit these in the script if needed:

```python
LEVERAGE = 5
TRADE_USD = 200
CONF_THRESHOLD = 0.7
LIVE_MODE = False  # Set to True to use real Binance orders (not recommended for testing)
```

---

## 📊 Logs

- All simulated trades are saved in `simulated_trade_log.csv`
- Each trade includes entry/exit prices, confidence, indicators, TP/SL, and final profit.

---

## 🔐 Optional: Enable Real Trading (NOT recommended without safeguards)

Set your Binance API keys as environment variables:

```bash
export BINANCE_API_KEY=your_key
export BINANCE_API_SECRET=your_secret
```

Then set `LIVE_MODE = True` in the script to execute real trades.

⚠️ Use at your own risk. Start small. Test thoroughly.

---

## 📅 Coming Soon Ideas

- Web-based dashboard to monitor trades live
- Strategy switching and multi-symbol learning
- Discord/Telegram alerts
- Backtesting module
