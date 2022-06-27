---
order: 95
---

# Contract

---

## Public

### Security: [None](basic-information/#endpoint-security-type)

Endpoints under **Public** section can be accessed freely without requiring any API-key or signatures.

#### Test Connectivity

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/ping**</font>
This endpoint checks connectivity to the host

---

**Parameters**

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Connection normal

==-

#### Check Server Time

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/time**</font>
This endpoint checks connectivity to the server and retrieves server timestamp

---

**Parameters**

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved server time

==-

#### Contract List

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/contracts**</font>
This endpoint retrieves all contracts list

---

**Parameters**

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved contracts list

==-

**Response**

name | type | example | description
---    | --- | --- | ---
symbol | string | ```E-BTC-USDT``` | Contract name
status | number | ```1``` | status 0: cannot trade </br> status 1: can trade
type | string | ```S``` | contract type, E: perpetual contract, S: test contract, others are mixed contract
side | number | ```1``` | Contract direction (backwards: 0, 1: forward)
multiply | number | ```0.5``` | Contract face value
multiplierCoin | string | ```BTC``` | Contract face value unit
pricePrecision | number | ```4``` | Precision of the price
minOrderVolume | number | ```10``` | Minimum order volume
minOrderMoney | number | ```10``` | Minimum order value
maxMarketVolume | number | ```100000``` | Market price order maximum volume
maxMarketMoney | number | ```100000``` | Market price order maximum value
maxLimitVolume | number | ```100000``` | Limit price order maximum volume
maxValidOrder | number | ```100000``` | Maximum valid order quantity

---

## Market

### Security Type: [None](basic-information/#endpoint-security-type)

**Market** section can be accessed freely without requiring any API-key or signatures.

#### Depth

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/depth**</font>
This endpoint retrieves market depth data

---

**Parameters**

**Query**

name | type | description
---    | --- | --- | ---
```contractName``` | string | Contract Name E.g. ```E-BTC-USDT```
```limit``` | integer | Default 100; Max 100

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved market depth data

==-

**Response**

name | type | example | description
---    | --- | --- | ---
time | long | ```1595563624731``` | Current timestamp (ms)
bids | list | Look below | Order book purchase info
asks | list | Look below | Order book selling info

The fields bids and asks are lists of order book price level entries, sorted from best to worst.

name | type | example | description
---    | --- | --- | ---
'' | float | ```131.1``` | price level
'' | float | ```2.3``` | Total order quantity for this price level

#### 24hrs ticker

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/ticker**</font>
24 hour price change statistics

---

**Parameters**

**Query**

name | type | description
---    | --- | --- | ---
```contractName``` | string | Contract  name E.g. ```E-BTC-USDT```

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully obtain ticker info

==-

**Response**

name | type | example | description
---    | --- | --- | ---
time | long | ```1595563624731``` | Open Time
high | float | ```9900``` | Higher Price
low | float | ```8800.34``` | Lowwe Price
last | float | ```8900``` | Newest Price
theft | float | ```4999``` | Trade Volume
rose | string | ```+0.5``` | Price variation

#### Get index/marked price

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/index**</font>

---

**Parameters**

**Query**

name | type | description
---    | --- | --- | ---
```contractName``` | string | Contract name E.g. ```E-BTC-USDT```
```limit``` | string | Default 100; Max 1000

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```indexPrice``` | float | ```0.055``` | Index price
```markPrice``` | float | ```0.0578``` | Marked price
```contractName``` | string | ```E-BTC-USDT``` | Contract name
```lastFundingRate``` | float | ```0.123``` | Current funding rate

#### Kline / Candlestick data

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/klines**</font>

---

**Parameters**

**Query**

name | type | description
---    | --- | --- | ---
```contractName``` | string | Contract name E.g. ```E-BTC-USDT```
```interval``` | integer | Interval of the Kline. Possible values include: ```1min```,```5min```,```15min```,```30min```,```60min```,```1day```,```1week```,```1month```
```limit``` | string | Default 100; Max 300

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```idx``` | long | ```1538728740000``` | Start timestamp (ms
```open``` | float | ```36.00000``` | Open price
```close``` | float | ```33.00000``` | Closing price
```high``` | float | ```36.00000``` | Max price
```low``` | float | ```30.00000``` | Min price
```vol``` | float | ```2456.111``` | Trade volume

---

## Trade

### Security Type: [TRADE](basic-information/#endpoint-security-type)

Endpoints under **Trade** require an [API-key and a signature.](basic-information/#signed-trade-and-user_data-endpoint-security)

#### Order creation

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/order**</font>

Creation of single new orders

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
contractName | string | Contract Name. E.g. ```E-BTC-USDT```
volume | number | Order quantity
price | number | Order price
type | string | Type of the order, ```LIMIT/MARKET```
side | string | Trade direction, ```BUY/SELL```
open | string | Open balancing direction, ```OPEN/CLOSE```
positionType | number | Hold-up position, ```1 full position, 2 restrictive position```
clientOrderId | string | Client order identity, a string with length less than 32 bit
timeInForce | integer | ```IOC, FOK, POST_ONLY```

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```orderId``` | string | ```256609229205684228``` | Order ID

#### Condition order creation

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/order/conditionOrder**</font>

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
contractName | string | Contract Name. E.g. ```E-BTC-USDT```
volume | number | Order quantity
price | number | Order price
type | string | Type of the order, ```LIMIT/MARKET```
side | string | Trade direction, ```BUY/SELL```
open | string | Open balancing direction, ```OPEN/CLOSE```
positionType | number | Hold-up position, ```1 full position, 2 restrictive position```
triggerPrice | string | Trigger price
triggerType | string | Trigger type ```3UP/4DOWN```

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

#### Cancel Orders

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/cancel**</font>

Rate limit: **20 times/ 2 seconds**

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
contractName | string | Contract Name. E.g. ```E-BTC-USDT```
orderId | string | Order ID

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

#### Order details

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/order**</font>

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
contractName | string | Contract Name. E.g. ```E-BTC-USDT```

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```orderId``` | long | ```150695552109032492``` | ID of the order
```contractName``` | string | ```E-BTC-USDT``` | Contract name
```price``` | float | ```10.5``` | Order price
```origQty``` | float | ```10.5``` | Order quantity
```executedQty``` | float | ```20``` | Order quantity
```avgPrice``` | float | ```10.5``` | Average transaction price
```status``` | string | ```NEW``` | Order status. Possible values are：```NEW```(new order，not filled), ```PARTIALLY_FILLED```(partially filled), ```FILLED```(fully filled), ```CANCELLED```(already cancelled）and ```REJECTED```(order rejected）
```side``` | string | ```BUY``` | Order direction. Possible values can only be：```BUY```(buy long) and ```SELL```(sell short)
```action``` | string | ```OPEN``` | ```OPEN/CLOSE```
```transactTime``` | long | ```1607702400000``` | Order creation time

#### Open order

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/openOrders**</font>

**Obtain open contract, the user's current order**

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
contractName | string | Contract Name. E.g. ```E-BTC-USDT```

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```orderId``` | long | ```150695552109032492``` | Order ID（system generated）
```contractName``` | string | ```E-BTC-USDT``` | Contract name
```price``` | float | ```4765.29``` | Order price
```origQty``` | float | ```1.01``` | Order quantity
```executedQty``` | float | ```1.01``` | Order quantity
```avgPrice``` | float | ```4754.24``` | Average transaction price
```type``` | float | ```LIMIT``` | Order type. Possible values can only be:```LIMIT```(limit price) and ```MARKET```(market price）
```side``` | string | ```BUY``` | Order direction. Possible values can only be：```BUY```(buy long) and ```SELL```(sell short)
```status``` | string | ```NEW``` | Order status. Possible values are：```NEW```(new order，not filled), ```PARTIALLY_FILLED```(partially filled), ```FILLED```(fully filled), ```CANCELLED```(already cancelled）and ```REJECTED```(order rejected)
```action``` | string | ```OPEN``` | ```OPEN/CLOSE```
```transactTime``` | long | ```1607702400000``` | Order creation time

#### Order history

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/orderHistorical**</font>

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
contractName | string | Contract Name. E.g. ```E-BTC-USDT```
limit | string | Lines per page, default 100, max 1000
fromId | long | Start retrieving from this Id

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

#### Profit history

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/profitHistorical**</font>

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
contractName | string | Contract Name. E.g. ```E-BTC-USDT```
limit | string | Lines per page, default 100, max 1000
fromId | long | Start retrieving from this Id

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

#### Order record

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/myTrades**</font>


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
contractName | string | Contract Name. E.g. ```E-BTC-USDT```
limit | string | Lines per page, default 100, max 1000
fromId | long | Start retrieving from this tradeId

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

**Response**

name | type | example | description
---    | --- | --- | ---
```symbol``` | string | ```ETHBTC``` | Coin name(trade pair)
```tradeId``` | number | ```28457``` | Trade ID
```bidId``` | long | ```150695552109032492``` | Buyer order ID
```askId``` | long | ```150695552109032493``` | Seller order ID
```bidUserId``` | integer | ```10024``` | Buyer user ID
```askUserId``` | integer | ```10025``` | Seller user ID
```price``` | float | ```4.01``` | Filled price
```qty``` | float | ```12``` | Trade quantity
```amount``` | float | ```5.38``` | Filled amount
```time``` | number | ```1499865549590``` | Trade time stamp
```fee``` | number | ```0.001``` | Trading fees
```side``` | string | ```BUY``` | Current order direction ```BUY``` purchase, ```SELL``` selling
```contractName``` | string | ```E-BTC-USDT``` | Contract name
```isMaker``` | boolean | ```true``` | Is it maker?
```isBuyer``` | boolean | ```true``` | Is it buyer?

---

## Account

### Security Type: [USER_DATA](basic-information/#endpoint-security-type)

Endpoints under **Account** require an [API-key and a signature.](basic-information/#signed-trade-and-user_data-endpoint-security)

#### Account information

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/fapi/v1/account**</font>

Rate limit: **20times/2s**

---

**Parameters**

**Query**</br>
<font size="2">**Header**</font>

name | type | description
---    | --- | --- | ---
X-CH-SIGN | string | Sign
X-CH-APIKEY | string | Your API-Key
X-CH-TS | integer | Timestamp

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Successfully retrieved account information

==-

**Response**

name | type | description
---    | --- | ---
```account``` | ```[]``` | Balance collection

```account``` field:

name | type | example | description
---    | --- | --- | ---
```marginCoin``` | string | ```USDT``` | Margin coin
```accountNormal``` | float | ```10.05``` | Balance account
```accountLock``` | float | ```10.07``` | Margin frozen account
```partPositionNormal``` | float | ```10.07``` | Restricted position margin balance
```totalPositionNormal``` | float | ```10.07``` | Full position initial margin
```achievedAmount``` | float | ```10.07``` | Profit and losses occurred
```unrealizedAmount``` | float | ```10.05``` | Unfilled profit and losses
```totalMarginRate``` | float | ```10.05``` | Full position margin rate
```totalEquity``` | float | ```10.07``` | Full position equity
```partEquity``` | float | ```10.07``` | Restricted position equity
```totalCost``` | float | ```10.07``` | Full position costs
```sumMarginRate``` | float | ```10.07``` | All accounts margin rate
```positionVos``` | [] |  | Position contract record

```positionVos``` field:

name | type | example | description
---    | --- | --- | ---
```contractId``` | integer | ```2``` | Contract id
```contractName``` | string | ```E-BTC-USDT``` | Contract name
```contractSymbol``` | string | ```BTC-USDT``` | Contract coin pair
```positions``` | [] |  | Position details

```positions``` field:

name | type | example | description
---    | --- | --- | ---
```id``` | integer | ```2``` | Position id
```uid``` | integer | ```10023``` | User ID
```positionType``` | integer | ```1``` | Hold position type (1 full，2 restrictive)
```side``` | string | ```SELL``` | Hold position direction ```SELL``` sell long, ```BUY``` buy short
```volume``` | float | ```1.05``` | Hold quantity
```openPrice``` | float | ```1.05``` | Open position price
```avgPrice``` | float | ```1.05``` | Hold average price
```closePrice``` | float | ```1.05``` | Balancing average price
```leverageLevel``` | float | ```1.05``` | Leverage multiple
```holdAmount``` | float | ```05``` | Hold position margin
```closeVolume``` | float | ```1.05``` | Balanced quantity
```pendingCloseVolume``` | float | ```1.05``` | The number of pending closing orders
```realizedAmount``` | float | ```1.05``` | Profit and losses occurred
```historyRealizedAmount``` | float | ```1.05``` | Historic accumulated profit and losses
```tradeFee``` | float | ```1.05``` | Trading fees
```capitalFee``` | float | ```1.05``` | Capital costs
```closeProfit``` | float | ```1.05``` | Balancing profit and loss
```shareAmount``` | float | ```1.05``` | Amount to share
```freezeLock``` | integer | ```0``` | Position freeze status: 0 normal, 1 liquidation freeze, 2 delivery freeze
```status``` | integer | ```0``` | Position effectiveness，0 ineffective 1 effective
```ctime``` | time | | Creation time
```mtime``` | time | | Update time
```brokerId``` | integer | ```1023``` | Client id
```lockTime``` | time | | Liquidation lock time
```marginRate``` | float | ```1.05``` | Margin rate
```reducePrice``` | float | ```1.05``` | Price reduction
```returnRate``` | float | ```1.05``` | Return rate (profit rate)
```unRealizedAmount``` | float | ```1.05``` | Unfilled profit and losses
```openRealizedAmount``` | float | ```1.05``` | Open position unfilled  profit and losses
```positionBalance``` | float | ```1.05``` | Position value
```indexPrice``` | float | ```1.05``` | Newest marked price
```keepRate``` | float | ```1.05``` | Scaled minimum kept margin rate
```maxFeeRate``` | float | ```1.05``` | Balancing maximum fees rate