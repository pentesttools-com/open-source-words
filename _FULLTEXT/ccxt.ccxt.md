CCXT – CryptoCurrency eXchange Trading Library A JavaScript / Python / PHP library for cryptocurrency trading and e-commerce with support for many bitcoin/ether/altcoin exchange markets and merchant APIs. The CCXT library is used to connect and trade with cryptocurrency / altcoin exchanges and payment processing services worldwide. It provides quick access to market data for storage, analysis, visualization, indicator development, algorithmic trading, strategy backtesting, bot programming, webshop integration and related software engineering. It is intended to be used by coders, developers, technically-skilled traders, data-scientists and financial analysts for building trading algorithms on top of it. Current feature list: support for many exchange markets, even more upcoming soon fully implemented public and private APIs for all exchanges all currencies, altcoins and symbols, prices, order books, trades, tickers, etc... optional normalized data for cross-exchange or cross-currency analytics and arbitrage an out-of-the box unified all-in-one API extremely easy to integrate works in Node 7.6+, Python 2 and 3, PHP 5.3+, web browsers ccxt on GitHub | Install | Usage | Manual | FAQ | Examples | Changelog | Contributing Supported Cryptocurrency Exchange Markets The ccxt library currently supports the following 123 cryptocurrency exchange markets and trading APIs: | | id | name | ver | doc | countries | |---------------------------------------------------------------------------------------------------------------------------|--------------------|------------------------------------------------------------------------------|:---:|:------------------------------------------------------------------------------------------------:|-----------------------------------------| | | _1broker | 1Broker | 2 | API | US | | | _1btcxe | 1BTCXE | * | API | Panama | | | acx | ACX | 2 | API | Australia | | | allcoin | Allcoin | 1 | API | Canada | | | anxpro | ANXPro | 2 | API | Japan, Singapore, Hong Kong, New Zealand| | | anybits | Anybits | * | API | Ireland | | | bibox | Bibox | 1 | API | China, US, South Korea | | | binance | Binance | * | API | Japan | | | bit2c | Bit2C | * | API | Israel | | | bitbank | bitbank | 1 | API | Japan | | | bitbay | BitBay | * | API | Malta, EU | | | bitfinex | Bitfinex | 1 | API | British Virgin Islands | | | bitfinex2 | Bitfinex v2 | 2 | API | British Virgin Islands | | | bitflyer | bitFlyer | 1 | API | Japan | | | bithumb | Bithumb | * | API | South Korea | | | bitkk | bitkk | 1 | API | China | | | bitlish | Bitlish | 1 | API | UK, EU, Russia | | | bitmarket | BitMarket | * | API | Poland, EU | | | bitmex | BitMEX | 1 | API | Seychelles | | | bitsane | Bitsane | * | API | Ireland | | | bitso | Bitso | 3 | API | Mexico | | | bitstamp | Bitstamp | 2 | API | UK | | | bitstamp1 | Bitstamp v1 | 1 | API | UK | | | bittrex | Bittrex | 1.1 | API | US | | | bitz | Bit-Z | 1 | API | Hong Kong | | | bl3p | BL3P | 1 | API | Netherlands, EU | | | bleutrade | Bleutrade | 2 | API | Brazil | | | braziliex | Braziliex | * | API | Brazil | | | btcbox | BtcBox | 1 | API | Japan | | | btcchina | BTCChina | 1 | API | China | | | btcexchange | BTCExchange | * | API | Philippines | | | btcmarkets | BTC Markets | * | API | Australia | | | btctradeim | BtcTrade.im | * | API | Hong Kong | | | btctradeua | BTC Trade UA | * | API | Ukraine | | | btcturk | BTCTurk | * | API | Turkey | | | btcx | BTCX | 1 | API | Iceland, US, EU | | | bxinth | BX.in.th | * | API | Thailand | | | ccex | C-CEX | * | API | Germany, EU | | | cex | CEX.IO | * | API | UK, EU, Cyprus, Russia | | | chbtc | CHBTC | 1 | API | China | | | chilebit | ChileBit | 1 | API | Chile | | | cobinhood | COBINHOOD | * | API | Taiwan | | | coinbase | coinbase | 2 | API | US | | | coinbasepro | Coinbase Pro | * | API | US | | | coincheck | coincheck | * | API | Japan, Indonesia | | | coinegg | CoinEgg | * | API | China, UK | | | coinex | CoinEx | 1 | API | China | | | coinexchange | CoinExchange | * | API | India, Japan, South Korea, Vietnam, US | | | coinfalcon | CoinFalcon | * | API | UK | | | coinfloor | coinfloor | * | API | UK | | | coingi | Coingi | * | API | Panama, Bulgaria, China, US | | | coinmarketcap | CoinMarketCap | 1 | API | US | | | coinmate | CoinMate | * | API | UK, Czech Republic, EU | | | coinnest | coinnest | * | API | South Korea | | | coinone | CoinOne | 2 | API | South Korea | | | coinsecure | Coinsecure | 1 | API | India | | | coinspot | CoinSpot | * | API | Australia | | | cointiger | CoinTiger | 1 | API | China | | | coolcoin | CoolCoin | * | API | Hong Kong | | | crypton | Crypton | 1 | API | EU | | | cryptopia | Cryptopia | * | API | New Zealand | | | deribit | Deribit | 1 | API | Netherlands | | | dsx | DSX | 3 | API | UK | | | ethfinex | Ethfinex | 1 | API | British Virgin Islands | | | exmo | EXMO | 1 | API | Spain, Russia | | | exx | EXX | * | API | China | | | fcoin | FCoin | 2 | API | China | | | flowbtc | flowBTC | 1 | API | Brazil | | | foxbit | FoxBit | 1 | API | Brazil | | | fybse | FYB-SE | * | API | Sweden | | | fybsg | FYB-SG | * | API | Singapore | | | gatecoin | Gatecoin | * | API | Hong Kong | | | gateio | Gate.io | 2 | API | China | | | gdax | GDAX | * | API | US | | | gemini | Gemini | 1 | API | US | | | getbtc | GetBTC | * | API | St. Vincent & Grenadines, Russia | | | hadax | HADAX | 1 | API | China | | | hitbtc | HitBTC | 1 | API | Hong Kong | | | hitbtc2 | HitBTC v2 | 2 | API | Hong Kong | | | huobi | Huobi | 3 | API | China | | | huobicny | Huobi CNY | 1 | API | China | | | huobipro | Huobi Pro | 1 | API | China | | | ice3x | ICE3X | * | API | South Africa | | | independentreserve | Independent Reserve | * | API | Australia, New Zealand | | | indodax | INDODAX | 1.8 | API | Indonesia | | | itbit | itBit | 1 | API | US | | | jubi | jubi.com | 1 | API | China | | | kraken | Kraken | 0 | API | US | | | kucoin | Kucoin | 1 | API | Hong Kong | | | kuna | Kuna | 2 | API | Ukraine | | | lakebtc | LakeBTC | 2 | API | US | | | lbank | LBank | 1 | API | China | | | liqui | Liqui | 3 | API | Ukraine | | | livecoin | LiveCoin | * | API | US, UK, Russia | | | luno | luno | 1 | API | UK, Singapore, South Africa | | | lykke | Lykke | 1 | API | Switzerland | | | mercado | Mercado Bitcoin | 3 | API | Brazil | | | mixcoins | MixCoins | 1 | API | UK, Hong Kong | | | negociecoins | NegocieCoins | 3 | API | Brazil | | | nova | Novaexchange | 2 | API | Tanzania | | | okcoincny | OKCoin CNY | 1 | API | China | | | okcoinusd | OKCoin USD | 1 | API | China, US | | | okex | OKEX | 1 | API | China, US | | | paymium | Paymium | 1 | API | France, EU | | | poloniex | Poloniex | * | API | US | | | qryptos | QRYPTOS | 2 | API | China, Taiwan | | | quadrigacx | QuadrigaCX | 2 | API | Canada | | | quoinex | QUOINEX | 2 | API | Japan, Singapore, Vietnam | | | southxchange | SouthXchange | * | API | Argentina | | | surbitcoin | SurBitcoin | 1 | API | Venezuela | | | therock | TheRockTrading | 1 | API | Malta | | | tidebit | TideBit | 2 | API | Hong Kong | | | tidex | Tidex | 3 | API | UK | | | urdubit | UrduBit | 1 | API | Pakistan | | | vaultoro | Vaultoro | 1 | API | Switzerland | | | vbtc | VBTC | 1 | API | Vietnam | | | virwox | VirWoX | * | API | Austria, EU | | | wex | WEX | 3 | API | New Zealand | | | xbtce | xBTCe | 1 | API | Russia | | | yobit | YoBit | 3 | API | Russia | | | yunbi | YUNBI | 2 | API | China | | | zaif | Zaif | 1 | API | Japan | | | zb | ZB | 1 | API | China | The list above is updated frequently, new crypto markets, altcoin exchanges, bug fixes, API endpoints are introduced and added on a regular basis. See the Manual for details. If you dont find a cryptocurrency exchange market in the list above and/or want another exchange to be added, post or send us a link to it by opening an issue here on GitHub or via email. The library is under MIT license, that means its absolutely free for any developer to build commercial and opensource software on top of it, but use it at your own risk with no warranties, as is. Install The easiest way to install the ccxt library is to use builtin package managers: ccxt in NPM (JavaScript / Node v7.6+) ccxt in PyPI (Python 2 and 3.5.3+) ccxt in Packagist/Composer (PHP 5.3+) This library is shipped as an all-in-one module implementation with minimalistic dependencies and requirements: js/ in JavaScript python/ in Python (generated from JS) php/ in PHP (generated from JS) You can also clone it into your project directory from ccxt GitHub repository: shell git clone https://github.com/ccxt/ccxt.git An alternative way of installing this library into your code is to copy a single file manually into your working directory with language extension appropriate for your environment. JavaScript (NPM) JavaScript version of CCXT works both in Node and web browsers. Requires ES6 and async/await syntax support (Node 7.6.0+). When compiling with Webpack and Babel, make sure it is not excluded in your babel-loader config. ccxt in NPM shell npm install ccxt ```JavaScript var ccxt = require (ccxt) console.log (ccxt.exchanges) // print all available exchanges ``` JavaScript (for use with the <script> tag): All-in-one browser bundle (dependencies included), served from unpkg CDN, which is a fast, global content delivery network for everything on NPM. HTML <script type="text/javascript" src="https://unpkg.com/ccxt"></script> Creates a global ccxt object: JavaScript console.log (ccxt.exchanges) // print all available exchanges Python ccxt in PyPI shell pip install ccxt Python import ccxt print(ccxt.exchanges) # print a list of all available exchange classes The library supports concurrent asynchronous mode with asyncio and async/await in Python 3.5.3+ Python import ccxt.async as ccxt # link against the asynchronous version of ccxt PHP ccxt in PHP with Packagist/Composer (PHP 5.3+) It requires common PHP modules: cURL mbstring (using UTF-8 is highly recommended) PCRE iconv PHP include "ccxt.php"; var_dump (\ccxt\Exchange::$exchanges); // print a list of all available exchange classes Documentation Read the Manual for more details. Usage Intro The ccxt library consists of a public part and a private part. Anyone can use the public part out-of-the-box immediately after installation. Public APIs open access to public information from all exchange markets without registering user accounts and without having API keys. Public APIs include the following: market data instruments/trading pairs price feeds (exchange rates) order books trade history tickers OHLC(V) for charting other public endpoints For trading with private APIs you need to obtain API keys from/to exchange markets. It often means registering with exchanges and creating API keys with your account. Most exchanges require personal info or identification. Some kind of verification may be necessary as well. If you want to trade you need to register yourself, this library will not create accounts or API keys for you. Some exchange APIs expose interface methods for registering an account from within the code itself, but most of exchanges dont. You have to sign up and create API keys with their websites. Private APIs allow the following: manage personal account info query account balances trade by making market and limit orders deposit and withdraw fiat and crypto funds query personal orders get ledger history transfer funds between accounts use merchant services This library implements full public and private REST APIs for all exchanges. WebSocket and FIX implementations in JavaScript, PHP, Python and other languages coming soon. The ccxt library supports both camelcase notation (preferred in JavaScript) and underscore notation (preferred in Python and PHP), therefore all methods can be called in either notation or coding style in any language. // both of these notations work in JavaScript/Python/PHP exchange.methodName () // camelcase pseudocode exchange.method_name () // underscore pseudocode Read the Manual for more details. JavaScript ```JavaScript use strict; const ccxt = require (ccxt); (async function () { let kraken = new ccxt.kraken () let bitfinex = new ccxt.bitfinex ({ verbose: true }) let huobi = new ccxt.huobi () let okcoinusd = new ccxt.okcoinusd ({ apiKey: YOUR_PUBLIC_API_KEY, secret: YOUR_SECRET_PRIVATE_KEY, }) console.log (kraken.id, await kraken.loadMarkets ()) console.log (bitfinex.id, await bitfinex.loadMarkets ()) console.log (huobi.id, await huobi.loadMarkets ()) console.log (kraken.id, await kraken.fetchOrderBook (kraken.symbols[0])) console.log (bitfinex.id, await bitfinex.fetchTicker (BTC/USD)) console.log (huobi.id, await huobi.fetchTrades (ETH/CNY)) console.log (okcoinusd.id, await okcoinusd.fetchBalance ()) // sell 1 BTC/USD for market price, sell a bitcoin for dollars immediately console.log (okcoinusd.id, await okcoinusd.createMarketSellOrder (BTC/USD, 1)) // buy 1 BTC/USD for $2500, you pay $2500 and receive ฿1 when the order is closed console.log (okcoinusd.id, await okcoinusd.createLimitBuyOrder (BTC/USD, 1, 2500.00)) // pass/redefine custom exchange-specific order params: type, amount, price or whatever // use a custom order type bitfinex.createLimitSellOrder (BTC/USD, 1, 10, { type: trailing-stop }) }) (); ``` Python ```Python coding=utf-8 import ccxt hitbtc = ccxt.hitbtc({verbose: True}) bitmex = ccxt.bitmex() huobi = ccxt.huobi() exmo = ccxt.exmo({ apiKey: YOUR_PUBLIC_API_KEY, secret: YOUR_SECRET_PRIVATE_KEY, }) kraken = ccxt.kraken({ apiKey: YOUR_PUBLIC_API_KEY, secret: YOUR_SECRET_PRIVATE_KEY, }) hitbtc_markets = hitbtc.load_markets() print(hitbtc.id, hitbtc_markets) print(bitmex.id, bitmex.load_markets()) print(huobi.id, huobi.load_markets()) print(hitbtc.fetch_order_book(hitbtc.symbols[0])) print(bitmex.fetch_ticker(BTC/USD)) print(huobi.fetch_trades(LTC/CNY)) print(exmo.fetch_balance()) sell one ฿ for market price and receive $ right now print(exmo.id, exmo.create_market_sell_order(BTC/USD, 1)) limit buy BTC/EUR, you pay €2500 and receive ฿1 when the order is closed print(exmo.id, exmo.create_limit_buy_order(BTC/EUR, 1, 2500.00)) pass/redefine custom exchange-specific order params: type, amount, price, flags, etc... kraken.create_market_buy_order(BTC/USD, 1, {trading_agreement: agree}) ``` PHP ```PHP include ccxt.php; $poloniex = new \ccxt\poloniex (); $bittrex = new \ccxt\bittrex (array (verbose => true)); $quoinex = new \ccxt\quoinex (); $zaif = new \ccxt\zaif (array ( apiKey => YOUR_PUBLIC_API_KEY, secret => YOUR_SECRET_PRIVATE_KEY, )); $hitbtc = new \ccxt\hitbtc (array ( apiKey => YOUR_PUBLIC_API_KEY, secret => YOUR_SECRET_PRIVATE_KEY, )); $poloniex_markets = $poloniex->load_markets (); var_dump ($poloniex_markets); var_dump ($bittrex->load_markets ()); var_dump ($quoinex->load_markets ()); var_dump ($poloniex->fetch_order_book ($poloniex->symbols[0])); var_dump ($bittrex->fetch_trades (BTC/USD)); var_dump ($quoinex->fetch_ticker (ETH/EUR)); var_dump ($zaif->fetch_ticker (BTC/JPY)); var_dump ($zaif->fetch_balance ()); // sell 1 BTC/JPY for market price, you pay ¥ and receive ฿ immediately var_dump ($zaif->id, $zaif->create_market_sell_order (BTC/JPY, 1)); // buy BTC/JPY, you receive ฿1 for ¥285000 when the order closes var_dump ($zaif->id, $zaif->create_limit_buy_order (BTC/JPY, 1, 285000)); // set a custom user-defined id to your order $hitbtc->create_order (BTC/USD, limit, buy, 1, 3000, array (clientOrderId => 123)); ``` Contributing Please read the CONTRIBUTING document before making changes that you would like adopted in the code. Also, read the Manual for more details. Support Developer Team We are investing a significant amount of time into the development of this library. If CCXT made your life easier and you like it and want to help us improve it further or if you want to speed up new features and exchanges, please, support us with a tip. We appreciate all contributions! Sponsors Support this project by becoming a sponsor. Your logo will show up here with a link to your website. [Become a sponsor] Backers Thank you to all our backers! [Become a backer] Crypto ETH 0xa7c2b18b7c8b86984560cad3b1bc3224b388ded0 BTC 33RmVRfhK2WZVQR1R83h2e9yXoqRNDvJva BCH 1GN9p233TvNcNQFthCgfiHUnj5JRKEc2Ze LTC LbT8mkAqQBphc4yxLXEDgYDfEax74et3bP Thank you!