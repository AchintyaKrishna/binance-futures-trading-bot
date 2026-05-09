# Trading Bot — Binance Futures Testnet

A Python CLI application to place Market and Limit orders on Binance Futures Testnet (USDT-M).

## Setup

**1. Clone and install dependencies**
```bash
git clone <your-repo-url>
cd trading_bot
pip install -r requirements.txt
```

**2. Configure API credentials**

Copy `.env.example` to `.env` and fill in your testnet keys:
```bash
cp .env.example .env
```

```
BINANCE_API_KEY=your_api_key
BINANCE_API_SECRET=your_api_secret
```

Get keys from: https://testnet.binancefuture.com → API Management

## Usage

```bash
python cli.py --symbol BTCUSDT --side BUY --type MARKET --quantity 0.01

python cli.py --symbol ETHUSDT --side SELL --type LIMIT --quantity 0.1 --price 3000
```

### All arguments

| Argument     | Required | Description                        |
|-------------|----------|------------------------------------|
| `--symbol`  | Yes      | Trading pair (e.g. BTCUSDT)        |
| `--side`    | Yes      | BUY or SELL                        |
| `--type`    | Yes      | MARKET or LIMIT                    |
| `--quantity`| Yes      | Order quantity                     |
| `--price`   | LIMIT only | Limit price                     |

## Logs

All logs written to `logs/trading_bot.log` (auto-created). Rotating file handler keeps last 5 × 2 MB files.

## Assumptions

- Testnet only — base URL hardcoded to `https://testnet.binancefuture.com`
- Valid symbols limited to: BTCUSDT, ETHUSDT, BNBUSDT, SOLUSDT, XRPUSDT
- LIMIT orders use `timeInForce=GTC` (Good Till Cancelled)
- Python 3.10+ required (uses `str | None` union syntax)