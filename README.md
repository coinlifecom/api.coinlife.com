# api.coinlife.com
Public REST API methods

**URL** `https://api.coinlife.com/public/{method}/..`


### `getTickers`
Real-time exchanges crypto currencies tickers

`../getTickers/{exchange}/{currency}/{order_value?}/{order_type?}`

**Posible values of parameters:**

`exchange` poloniex, binance, bitstamp, bittrex, kraken, bitfinex

`currency` BTC, USD, EUR, CNY, RUB, KZT, UAH, GEL

`order_value` volume, price, change, name, symbol `default = volume`

`order_type` desc, asc `default = desc`

Parameters without `?` is required

**JSON Response example**

**GET** `https://api.coinlife.com/public/getTickers/kraken/BTC`

```
{
  "status": "ok",
  "tickers": {
    "BTC_XDG": {
      "change_tag": "down",
      "change": "-3.39",
      "name": "Dogecoin",
      "last": "0.00000057",
      "volume": "8635996.03",
      "currency": "XDG"
    },
    ...
  }
}
```

### `getGraph`
Real-time date-value graph data

`../getGraph/{crypto_currency}/{parameter}`

**Posible values of parameters:**

`crypto_currency` BTC, LTC, ETH, BCH, DASH ... all crypto currencies symbols you can get in [https://api.coinlife.com/public/getStats](https://api.coinlife.com/public/getStats)

`parameter` hashrate, marketcap, transactions_1h

All parameters is required

**JSON Response example**

**GET** `https://api.coinlife.com/public/getGraph/BTC/transactions_1h`

```
{
  "status": "ok",
  "props": {
    "value": "219.48K",
    "name": "total transactions (24h)",
    "percent_change": 22.87
  },
  "options": {
    "x": {
      "min": 1519727401,
      "max": 1519810202
    },
    "y": {
      "min": 8680,
      "max": 9727
    }
  },
  "graph": [{
    "x": 1519727401,
    "y": 8691
  },
  ...
  ]
}
```



### `getStats`
Current crypto currencies statistics

`../getStats`

**No parameters**

**JSON Response example**

**GET** `https://api.coinlife.com/public/getStats`

```
{
  "status": "ok",
  "stats": {
    "BTC": {
      "id": "151735",
      "date": "2018-02-28 06:55:02",
      "symbol": "BTC",
      "symbol_hash": "4b9169eb3e07e0e885eb62f7bfc41a33",
      "total": "16878023",
      "price": "10914.24",
      "marketcap": "184210714133",
      "transactions_24h": "223838",
      "transactions_1h": "9327",
      "turnhover_24h": "967703",
      "turnhover_1h": "40321",
      "amount": "4.32",
      "amount_median": "0.082",
      "block_time": "505.00",
      "total_blocks": "511283",
      "total_blocks_24h": "170",
      "total_blocks_1h": "7",
      "block_reward": "12.81",
      "block_reward_24h": "54.10",
      "difficulty": "3007383866430",
      "hashrate": "2.4459e19",
      "mining_profit": "0.0000000000009715"
    },
    ...
  }
}
```

### `getMarketcap`

Crypto currencies marketcap

`../getMarketcap`

**No parameters**

**JSON Response example**

**GET** `https://api.coinlife.com/public/getMarketcap`

```
{
  "status": "ok",
  "marketcap": {
    "currencies": [{
      "id": "bitcoin",
      "name": "Bitcoin",
      "symbol": "BTC",
      "rank": "1",
      "price_usd": "10727.7",
      "price_btc": "1.0",
      "24h_volume_usd": "7155650000.0",
      "market_cap_usd": "181203189855",
      "available_supply": "16891150.0",
      "total_supply": "16891150.0",
      "max_supply": "21000000.0",
      "percent_change_1h": "-0.92",
      "percent_change_24h": "0.58",
      "percent_change_7d": "-3.75",
      "last_updated": "1519807767"
    },
    ...
    ],
    "global": {
      "total_market_cap_usd": 453012789938,
      "total_24h_volume_usd": 18224909442,
      "bitcoin_percentage_of_market_cap": 39.85,
      "active_currencies": 912,
      "active_assets": 611,
      "active_markets": 8846,
      "last_updated": 1519808069
    }
  }
}
```

### `getPools`
Mining pools rating and statistics

`../getPools/{interval?}/{history_year?}`

**Posible values of parameters:**

`interval` 1D, 3D, 1W, 1M, 3M, 1Y, ALL `default = 1D`

`history_year` 2009, 2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, latest `default = latest`

Parameters without `?` is required

**JSON Response example**

**GET** `https://api.coinlife.com/public/getPolls/1D`

```
{
  "status": "ok",
  "pools": {
    "pools": [{
      "n": "48",
      "p": 0.29268292682927,
      "name": "BTC.com",
      "id": "55",
      "hash_share": 7.0730604419984e+18,
      "count": "48"
    },
    ...
    ],
  },
  "history" : {
    "BTC.com": ["0.0440","0.0426","0.0637","0.0767","0.0819","0.1173","0.1158","0.1142","0.1438","0.1710","0.2204","0.2598"],
    "AntPool": ["0.1576","0.1654","0.1630","0.1673","0.2120","0.1825","0.1580","0.1922","0.1742","0.1788","0.1899","0.1536"],
    ...
  }
}
```
