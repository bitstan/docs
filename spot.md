---
order: 97
---

# Spot

---

## Public

### Security: [None](basic-information/#endpoint-security-type)

Endpoints under **Public** section can be accessed freely without requiring any API-key or signatures.

#### Test Connectivity

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/ping**</font>
This endpoint checks connectivity to the host

sdk: [TestConnectivity.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/TestConnectivity.java)

---

**Parameters**

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Connection normal

==-

#### Check Server Time

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/time**</font>
This endpoint checks connectivity to the server and retrieves server timestamp

sdk: [CheckServerTime.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/CheckServerTime.java)

---

**Parameters**

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved server time

==-

#### Pairs List

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/symbols**</font>
This endpoint retrieves coin pairs list

sdk: [PairsList.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/PairsList.java)

---

**Parameters**

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved pairs list

==-

**Response**

name | type | example | description
---    | --- | --- | ---
symbol | string | ```BTCUSDT``` | Name of the symbol
baseAsset | string | ```BTC``` | Underlying asset for the symbol
quoteAsset | string | ```USDT``` | Quote asset for the symbol
pricePrecision | integer | ```2``` | Precision of the price
quantityPrecision | integer | ```6``` | Precision of the quantity

---

## Market

### Security Type: [None](basic-information/#endpoint-security-type)

**Market** section can be accessed freely without requiring any API-key or signatures.

#### Depth

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/depth**</font>
This endpoint retrieves market depth data

sdk: [Depth.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/Depth.java)

---

**Parameters**

**Query**

name | type | description
---    | --- | --- | ---
```symbol``` | string | Symbol name E.g. ```BTCUSDT```
```limit``` | integer | Default 100; Max 100

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved market depth data

==-

**Response**

name | type | example | description
---    | --- | --- | ---
time | long | ```1595563624731``` | Current timestamp (ms)
bids | list | ; | List of all bids, best bids first. See below for entry details.
asks | list | ; | List of all asks, best asks first. See below for entry details.

The fields bids and asks are lists of order book price level entries, sorted from best to worst.

name | type | example | description
---    | --- | --- | ---
'' | float | ```131.1``` | price level
'' | float | ```2.3``` | The total quantity of orders for this price level

#### 24hrs ticker

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/ticker**</font>
24 hour price change statistics

sdk: [Ticker.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/Ticker.java)

---

**Parameters**

**Query**

name | type | description
---    | --- | --- | ---
```symbol``` | string | Symbol name E.g. ```BTCUSDT```

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved ticker data

==-

**Response**

name | type | example | description
---    | --- | --- | ---
time | long | ```1595563624731``` | Open Time
high | float | ```9900``` | High Price
low | float | ```8800.34``` | Low Price
last | float | ```8900``` | Last Price
vol | float | ```4999``` | Trade Volume

#### Recent Trades List

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/trades**</font>

sdk: [RecentTradesList.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/RecentTradesList.java)

---

**Parameters**

**Query**

name | type | description
---    | --- | --- | ---
```symbol``` | string | Symbol name E.g. ```BTCUSDT```
```limit``` | string | Default 100; Max 1000

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```price``` | float | ```0.055``` | The price of the trade
```time``` | long | ```1537797044116``` | Current timestamp (ms)
```qty``` | float | ```5``` | The quantity traded
```side``` | string | ```BUY/SELL``` | Taker side

#### Kline / Candlestick data

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/klines**</font>

sdk: [KlineCandlestickData.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/KlineCandlestickData.java)

---

**Parameters**

**Query**

name | type | description
---    | --- | --- | ---
```symbol``` | string | Symbol name E.g. ```BTCUSDT```
```interval``` | integer | Interval of the Kline. Possible values include: ```1min```,```5min```,```15min```,```30min```,```60min```,```1day```,```1week```,```1month```
```limit``` | string | Default 100; Max 300

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```idx``` | long | ```1538728740000``` | Open time
```open``` | float | ```36.00000``` | Open price
```close``` | float | ```33.00000``` | Close price
```high``` | float | ```36.00000``` | High price
```low``` | float | ```30.00000``` | Low price
```vol``` | float | ```2456.111``` | Volume

---

## Trade

### Security Type: [TRADE](basic-information/#endpoint-security-type)

Endpoints under **Trade** require an [API-key and a signature.](basic-information/#signed-trade-and-user_data-endpoint-security)

#### New Order

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/order**</font>

Rate Limit: **100times/2s**

sdk: [NewOrder.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/NewOrder.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

name | type | description
---    | --- | --- | ---
symbol | string | Symbol Name. E.g. ```BTCUSDT```
volume | number | Order vol. For MARKET BUY orders,  vol=amount.
side | string | Side of the order, ```BUY/SELL```
type | string | Type of the order, ```LIMIT/MARKET```
price | number | Order price, REQUIRED for LIMIT orders
newClientOrder | string | Unique order ID generated by users to mark their orders
recvWindow | integer | Time window

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully post new order

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```orderId``` | long | ```150695552109032492``` | ID of the order
```clientOrderId``` | string | ```213443``` | A unique ID of the order.
```symbol``` | string | ```BTCUSDT``` | Symbol Name
```transactTime``` | integer | ```1273774892913``` | Time the order is placed
```price``` | float | ```4765.29``` | Price of the order
```origQty``` | float | ```1.01``` | Quantity ordered
```executedQty``` | float | ```1.01``` | Quantity of orders that has been executed
```type``` | string | ```LIMIT``` | Order type ```LIMIT```, ```MARKET```
```side``` | string | ```BUY``` | Order side：```BUY```, ```SELL```
```status``` | string | ```NEW``` | The state of the order. Possible values include ```NEW```, ```PARTIALLY_FILLED```, ```FILLED```, ```CANCELED``` and ```REJECTED```.

#### Test New Order

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/order/test**</font>

Test new order creation and signature/recvWindow length. Creates and validates a new order but does not send the order into the matching engine.

sdk: [TestNewOrder.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/TestNewOrder.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

name | type | description
---    | --- | --- | ---
recvWindow | integer | Time window
symbol | string | Symbol Name. E.g. ```BTCUSDT```
volume | number | Order vol. For MARKET BUY orders,  vol=amount.
side | string | Side of the order, ```BUY/SELL```
type | string | Type of the order, ```LIMIT/MARKET```
price | number | Order price, REQUIRED for LIMIT orders
newClientOrder | string | Unique order ID generated by users to mark their orders

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully test new order

==-

#### Batch Orders

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/batchOrders**</font>

Rate Limit: **50times/2s A batch contains at most 10 orders**

sdk: [BatchOrders.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/BatchOrders.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

name | type | description
---    | --- | --- | ---
orders | array | Batch order param
symbol | string | Symbol Name. E.g. ```BTCUSDT```

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Request ```orders``` field:**

name | type | example | description
---    | --- | --- | ---
```price``` | float | ```1000``` | Price of the order
```volume``` | float | ```20.1``` | Vol of the order
```side``` | string | ```BUY/SELL``` | Side of the order
```batchType``` | string | ```LIMIT/MARKET``` | Batch type of the order

#### Query Order

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/order**</font>

Rate Limit: **20times/2s**

sdk: [QueryOrder.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/QueryOrder.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

name | type | description
---    | --- | --- | ---
orderId | array | Order ID
newClientOrderId | string | Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444
symbol | string | Symbol Name. E.g. ```BTCUSDT```

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```orderId``` | long | ```150695552109032492``` | ID of the order
```clientOrderId``` | string | ```213443``` | A unique ID of the order.
```symbol``` | string | ```BTCUSDT``` | Symbol Name
```price``` | float | ```4765.29``` | Price of the order
```origQty``` | float | ```1.01``` | Quantity ordered
```executedQty``` | float | ```1.01``` | Quantity of orders that has been executed
```avgPrice``` | float | ```4754.24``` | Average price of filled orders.
```type``` | string | ```LIMIT``` | Order type ```LIMIT```, ```MARKET```
```side``` | string | ```BUY``` | Order side：```BUY```, ```SELL```
```status``` | string | ```NEW``` | The state of the order. Possible values include ```NEW```, ```PARTIALLY_FILLED```, ```FILLED```, ```CANCELED``` and ```REJECTED```.

#### Cancel Order

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/cancel**</font>

Rate Limit: **100time/2s**

sdk: [CancelOrder.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/CancelOrder.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

name | type | description
---    | --- | --- | ---
orderId | array | Order ID
newClientOrderId | string | Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444
symbol | string | Symbol Name. E.g. ```BTCUSDT```

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Order cancellation successful

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```orderId``` | long | ```150695552109032492``` | ID of the order
```clientOrderId``` | string | ```213443``` | A unique ID of the order.
```symbol``` | string | ```BTCUSDT``` | Symbol Name
```status``` | string | ```NEW``` | The state of the order. Possible values include ```NEW```, ```PARTIALLY_FILLED```, ```FILLED```, ```CANCELED``` and ```REJECTED```.

#### Batch cancel orders

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/cancel**</font>

Rate Limit: **50times/2s A batch contains at most 10 orders**

sdk: [BatchCancelOrders.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/BatchCancelOrders.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

name | type | description
---    | --- | --- | ---
orderId | array | Order ID collection ```[123,456]```
symbol | string | Symbol Name. E.g. ```BTCUSDT```

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Batch order cancellation successful

==-

#### Current open Orders

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/openOrders**</font>

Rate Limit: **20times/2s**

sdk: [CurrentOpenOrders.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/CurrentOpenOrders.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

name | type | description
---    | --- | --- | ---
symbol | string | Symbol Name. E.g. ```BTCUSDT```
limit | integer | Default 100; Max 1000

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```orderId``` | long | ```150695552109032492``` | ID of the order
```clientOrderId``` | string | ```213443``` | A unique ID of the order.
```symbol``` | string | ```BTCUSDT``` | Symbol Name
```price``` | float | ```4765.29``` | Price of the order
```origQty``` | float | ```1.01``` | Quantity ordered
```executedQty``` | float | ```1.01``` | Quantity of orders that has been executed
```avgPrice``` | float | ```4754.24``` | Average price of filled orders.
```type``` | string | ```LIMIT``` | Order type ```LIMIT```, ```MARKET```
```side``` | string | ```BUY``` | Order side：```BUY```, ```SELL```
```status``` | string | ```NEW``` | The state of the order. Possible values include ```NEW```, ```PARTIALLY_FILLED```, ```FILLED```, ```CANCELED``` and ```REJECTED```.

#### Trades

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/myTrades**</font>

Rate Limit: **20times/2s**

sdk: [Trades.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/Trades.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

name | type | description
---    | --- | --- | ---
symbol | string | Symbol Name. E.g. ```BTCUSDT```
limit | integer | Default 100; Max 1000
fromId | integer | Trade Id to fetch from

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```symbol``` | string | ```ETHBTC``` | Symbol Name
```id``` | integer | ```28457``` | Trade ID
```bidId``` | long | ```150695552109032492``` | Bid Order ID
```askId``` | long | ```150695552109032493``` | Ask Order ID
```price``` | integer | ```4.01``` | Price of the trade
```qty``` | float | ```12``` | Quantity of the trade
```time``` | number | ```1499865549590``` | Timestamp of the trade
```isBuyer``` | bool | ```true``` | ```true``` = Buyer </br>```false``` = Seller
```isMaker``` | bool | ```false``` | ```true``` = Maker</br>```false``` = Taker
```feeCoin``` | string | ```ETH``` | Trading fee coin
```fee``` | number | ```0.001``` | Trading fee

---

## Account

### Security Type: [USER_DATA](basic-information/#endpoint-security-type)

Endpoints under **Account** require an [API-key and a signature.](basic-information/#signed-trade-and-user_data-endpoint-security)

#### Account information

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/account**</font>

Rate Limit: **20times/2s**

sdk: [AccountInformation.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/AccountInformation.java)

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

<font size="2">**Body**</font>

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved account information

==-

**Response**

name | type | description
---    | --- | ---
```balances``` | ```[]``` | Show balance details

```balances``` field:

name | type | example | description
---    | --- | --- | ---
```asset``` | string | ```USDT``` | Name of the asset
```free``` | float | ```1000.30``` | Amount available for use
```locked``` | float | ```400``` | Amount locked (for open orders)