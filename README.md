# opportunity detector and automated trading

raven，权利的游戏里的渡鸦，可以洞察世间的一切，而crypto-raven寓意洞察全球区块链资产里价差并进行套利活动。

It gets order books from supported exchanges and calculate arbitrage
opportunities between each markets. It takes market depth into account.

Currently supported exchanges to get data:
 - Bitfinex (BCH_BTC)
 - Bitfinex (BTC_USD)
 - Bittrex (BCH_BTC)
 - Bitstamp (USD)
 - BTC-e (USD)
 - OkCoin (CNY)
 - Huobi (CNY)
 - Broker (CNY)
 - Bitstar (Future)

Currently supported exchanges to automate trade:
 - Bitfinex (BCH_BTC)
 - Bitfinex (BTC_USD)
 - Bittrex (BCH_BTC)
 - Bitstamp (USD)
 - OkCoin (CNY)
 - Huobi (CNY)
 - Bitstar (Future)

# WARNING

**Real trading bots are included. Don't put your API keys in config.py
  if you don't know what you are doing.**

# Installation And Configuration

    $ cp arbitrage/config.py-example arbitrage/config.py

Then edit config.py file to setup your preferences: watched markets
and observers

You need Python3 to run this program. To install on Debian, Ubuntu, or
variants of them, use:

    $ sudo apt-get install python3 python3-pip python-nose
    $ pip3 install requests zmq

You need market broker service, please read its README to install then run it. 
  
    https://github.com/philsong/bitcoin-broker 

To connect the broker server you will need to install thriftpy:

    $ pip3 install cython thriftpy

To use the observer XMPPMessager you will need to install sleekxmpp:

    $ pip3 install sleekxmpp

# Run

To run the opportunity watcher:

    $ python3 arbitrage/arbitrage.py watch -v

To check your balance on an exchange (also a good way to check your accounts configuration):

    $ python3 arbitrage/arbitrage.py -m HaobtcCNY get-balance
    $ python3 arbitrage/arbitrage.py -m Bitfinex_BCH_BTC get-balance
    $ python3 arbitrage/arbitrage.py -m HaobtcCNY,BitstampUSD get-balance
    $ python3 arbitrage/arbitrage.py -m HaobtcCNY,OkCoinCNY,HuobiCNY get-balance

Run tests

    $ nosetests arbitrage/

# Alternative usage

List supported public markets:

      $ python3 arbitrage/arbitrage.py list-public-markets

Help
      
      $ python3 arbitrage/arbitrage.py -h

# Example

arbitrage in haobtc, huobi or okcoin

    $ python3 arbitrage/arbitrage.py -oTraderBot -mHaobtcCNY,HuobiCNY
    $ python3 arbitrage/arbitrage.py -oTraderBot -mHaobtcCNY,OKCoinCNY

balance statatistic 

    $ python3 arbitrage/arbitrage.py -oBalanceDumper -mHaobtcCNY
    
bistar test

    $ python3 arbitrage/bitstar_test.py

    
# TODO

 * Tests
 * Write documentation
 * Add other exchanges:
   * okex
 * Update order books with a WebSocket client for supported exchanges
 * Better history handling for observer "HistoryDumper" (Redis ?)
 * Move EUR / USD from a market to an other:
   * Coupons
   * Negative Operations
 * use Ethercoin or other cryptocurrencies for triangular arbitrage

# LICENSE


MIT

Copyright (c) 2016 Phil Song <songbohr@gmail.com>


Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Donate

If for some reason you feel like donating a few micro btc to future development, those should go here:

`1NDnnWCUu926z4wxA3sNBGYWNQD3mKyes8`

## Credits

* @[Maxime Biais](https://github.com/maxme) for [the original work on **bitcoin-arbitrage**](https://github.com/maxme/https://github.com/maxme/bitcoin-arbitrage)
