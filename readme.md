FFFF    AAAAA  M   M       AAAAA  RRRR   BBBB   III TTTTT RRRR    AAAAA  GGGG  EEEEE      BBBB   OOO  TTTTT
F      A     A MM MM      A     A R   R  B   B   I    T   R   R  A     A G     E          B   B O   O   T  
FFF    AAAAAAA M M M      AAAAAAA RRRR   BBBB    I    T   RRRR   AAAAAAA G  GG EEEE       BBBB  O   O   T  
F      A     A M   M      A     A R  R   B   B   I    T   R  R   A     A G   G E          B   B O   O   T  
F      A     A M   M      A     A R   R  BBBB   III   T   R   R  A     A  GGG  EEEEE      BBBB   OOO    T  


## Features
-  Comaptible with all ccxt exchanges.
-  Precise at the orderbook lever (close to a market-making algorithm)
-  Can work with an unlimited number of exchanges at the same time
-  Does a balance simulation for every possible opportunity to always choose the most profitable one
-  Full logging system

## Prerequistics
 - Install python 3.12

## Installation
1. Clone the repository

  git clone https://github.com/idealbridgex0/fam-arbitrage-bot.git

2. Go to the repository you just cloned

  cd fam-arbitrage-bot

3. Install the requirements to run the arbitrage system

  pip install  -r requirements.txt

4. Set your configuration details in exchange_config.py

5. Run with:

  Python run.py


## How to add an exchange?

1. Go to the exchange\_config.py file with any text editor
2. Locate the ‘exchanges’ variable
3. Add you api keys if you want it to trade with your account

  exchanges = {
    'kucoin':{},
    'binance':{},
    'okx':{},
    'poloniex':{},
    # 'another_exchange_here':{
    #     'apiKey':'here',
    #     'secret':'here',
    # },
  }


## Usage
You can also run it with one line like this:

  python run.py <mode> [renew-time-minutes] <balance-usdt-to-use> <pair> <exchanges list separated by commas (no space!)>
  
  - <mode> = the mode you wanna use between fake-money and real. See #full-version for real mode.

    * fake-money: will run the bot with the balance-usdt-to-use you put, with a virtual balance, just to test.
    * real: will run the bot with real money.
    
  - [renew-time-minutes] = ONLY IF YOU ENABLED RENEWAL SETTING IN THE CONFIG. If you enabled it, you have to put the number of minutes a session should last. After each session, the bot sells all the assets back to rebalance. Note: you can trigger a manual rebalance while in a session by pressing the Enter key.

  - <balance-usdt-to-use> = If you set the balance to 10,000 across two accounts, you need to deposit 5,000 into each exchange for the bot to function properly.

  - <pair> = The pair you wanna arbitrage on.
    ex: COMAI/USDT, BTC/USDT, ETH/USDT

  - <exchanges list> = the exchanges you want the bot to scan the orderbooks on, among all the CCXT-compatible exchanges. From a 2 exchanges minimum, up to an unlimited number. Don't forget to configure the exchanges in exchange_config.py.
  
  * Examples:
    @ Before this command you should enable renewal in the exchange_config.py
  
      python run.py real 15 1000 SOL/USDT binance,poloniex,kucoin   # run the bot with 1000 USDT on binance phemex and bybit on SOL/USDT, and rebalance every 15 minutes.