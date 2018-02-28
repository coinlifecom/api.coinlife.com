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


