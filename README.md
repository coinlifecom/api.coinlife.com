# api.coinlife.com
Public REST API methods

**URL** `https://api.coinlife.com/{method}...`

## `posts`
Get last N posts

`../posts?_sort=createdAt:desc&_limit={limit}`

`limit` 0,1,2...N Limit the size of the returned posts.

**JSON Response example**
### get last 10 posts
**GET** `https://api.coinlife.com/posts?_sort=createdAt:desc&_limit=10`

```
[
  {
    "_id": "5afd93e7c8efc34f391e5290",
    "post_id": 4600,
    "__v": 0,
    "author": {"1": "Author Name" },
    "categories": { "14": "News" },
    "tags": {"18": "биткоин", "26": "криптовалюта", "28": "майнинг"},
    "content": {},
    "createdAt": "2018-05-17T14:38:31.763Z",
    "date": "2018-05-17T17:37:07.000Z",
    "date_gmt": "2018-05-17T14:37:07.000Z",
    "excerpt": {},
    "featured_media": {},
    "format": "standard",
    "guid": {},
    "status": "publish",
    ...
  },
  ...
]
```

Get post by ID
`../posts/{post_id}`

`post_id` 0,1,2...N Unique identifier for a particular post.

**JSON Response example**
### get a post with id 4600
**GET** `https://api.coinlife.com/posts/4600`

```
{
  "_id": "5afd93e7c8efc34f391e5290",
  "post_id": 4600,
  "__v": 0,
  "author": {"1": "Author Name" },
  "categories": { "14": "News" },
  "tags": {"18": "биткоин", "26": "криптовалюта", "28": "майнинг"},
  "content": {},
  "createdAt": "2018-05-17T14:38:31.763Z",
  "date": "2018-05-17T17:37:07.000Z",
  "date_gmt": "2018-05-17T14:37:07.000Z",
  "excerpt": {},
  "featured_media": {},
  "format": "standard",
  "guid": {},
  "status": "publish",
  ...
}
```

## `charts`
get coins market data and chart

`../charts?createdAt_gte={date}&_sort=market_cap_usd:desc&_start={start}&_limit={limit}`

**Posible values of parameters:**

`date` YYYY-MM-DD format

`start` 0,1,2...N Skip a specific number of coins (especially useful for pagination).

`limit` 0,1,2...N Limit the size of the returned results.

**JSON Response example**
#### Get top 10 cryptocoins with chart data
**GET** `https://api.coinlife.com/charts?createdAt_gte=2018-05-17&_sort=market_cap_usd:desc&_limit=10`

```
[
  {
    "_id": "ethereum",
    "name": "Ethereum",
    "symbol": "ETH",
    "market_cap_usd": 70423230791,
    "price_usd": "707.817",
    "percent_change_24h": 1.52,
    "24h_volume_usd": 2251900000,
    "available_supply": 99493557,
    "data": [{
      "price_usd": "751.736",
      "createdAt": "2018-05-10T00:00:00.000Z"
      },
      {
      "price_usd": "755.771",
      "createdAt": "2018-05-10T01:00:00.000Z"
      },
      {
      "price_usd": "758.647",
      "createdAt": "2018-05-10T02:00:00.000Z"
      }
      ...
    ]
    ....
  }
  ....
]
```

## `currencyrate`

Using this query all quote values will be returned relative to the source currency you specified
`../currencyrate/{source}`

**Posible values of source parameter:**
`source` USD, EUR, RUB... etc

**JSON Response example**
#### Get all quotes
**GET** `https://api.coinlife.com/currencyrate/USD`

```
{
  "_id": "5b0307c2c8efc34f3920e9df",
  "source": "USD",
  "__v": 0,
  "createdAt": "2018-05-21T17:54:10.229Z",
  "quotes": {
    "USDAED": 3.672705,
    "USDAFN": 71.099998,
    "USDALL": 107.610001,
    "USDAMD": 482.529999,
    "USDANG": 1.787502,
    "USDAOA": 233.524994,
    "USDARS": 24.35695,
    "USDAUD": 1.321017,
    "USDAWG": 1.78,
    "USDAZN": 1.699503,
    "USDBAM": 1.6639,
    ...
  },
  "updatedAt": "2018-05-21T18:00:01.243Z"
}
```

Limit your API request to a set of specific currencies by attaching the quotes parameter followed by any available 3-letter currency codes (divided by commas) of your choice.
`../currencyrate/{source}?quotes=EUR,GBP,RUB,AUD`

**JSON Response example**
#### Get specific quotes
**GET** `https://api.coinlife.com/currencyrate/USD/?quotes=EUR,GBP,RUB,AUD`

```
{
  "_id": "5b0307c2c8efc34f3920e9df",
  "source": "USD",
  "quotes": {
    "USDEUR": 0.849295,
    "USDGBP": 0.74537,
    "USDRUB": 61.598202,
    "USDAUD": 1.321017
  },
  "createdAt": "2018-05-21T17:54:10.229Z",
  "updatedAt": "2018-05-21T18:00:01.243Z",
}
```


## `calc`

Get coins price, difficulty, reward for calculations data
`../calc`

**JSON Response example**
#### Get coins calculations data 
**GET** `https://api.coinlife.com/calc`

```
{
  "BTC": {
    "_id": "5b030b79c8efc34f3920ebce",
    "name": "Bitcoin",
    "symbol": "BTC",
    "block_reward": "12.72",
    "block_reward24": "12.686828440367",
    "difficulty": "4143878474754",
    "difficulty24": "4143878474754",
    "price_btc": "1.0",
    "price_usd": "8414.65",
    "createdAt": "2018-05-21T18:10:01.143Z",
    "updatedAt": "2018-05-21T18:10:01.143Z",
  },
  "BCH": {
  }
  ...
}
```


## `calc/presets`

Get all coins calc presets
`../calc/presets`

**JSON Response example**
#### Get all presets 
**GET** `https://api.coinlife.com/calc/presets`

```
[
  {
    "_id": "5b02ff7f019245423b496dc0",
    "symbol": "BTC",
    "hashrate": 13.5,
    "hashrate_select": "TH/s",
    "power_consump": 1323,
    "power_price": 0.07,
    "currency_selector": "USD",
    "whattomine_coin_name": "Bitcoin",
    "enable": true,
    "createdAt": "2018-05-21T17:18:55.346Z",
    "updatedAt": "2018-05-21T17:18:55.362Z",
    "__v": 0,
    "id": "5b02ff7f019245423b496dc0"
  },
  {
    "_id": "5b02ffd2019245423b496dc1",
    "symbol": "BCH",
    ....
  }
  ...
]
```

###### For more info read the Strapi filter concepts: https://strapi.io/documentation/guides/filters.html
