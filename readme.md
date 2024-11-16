

## How to add an exchange?

1. Go to the exchange\_config.py file with any text editor.
1. Locate the ‘exchanges’ variable.
1. Add you api keys if you want it to trade with your account.


## how to run bot?
1. Install python version 3.12.0
2. Install the requirements. pip install -r requirements.txt
3. Modify exchanes (apiKey, secret)
4. Run the bot
  python run.py <mode> [renew-time-minutes] <balance-usdt-to-use> <pair> <exchanges list separated by commas (no space!)>
  python run.py real 15 1000 COMAI/USDT binance,kucoin

  If you're using two exchanges with a balance of 1000, you'll need to deposit 500 USDT into each exchange.