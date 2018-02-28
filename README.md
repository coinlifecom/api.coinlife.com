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
