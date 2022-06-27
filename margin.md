---
order: 96
---

# Margin

---

## Trade

### Security Type: [TRADE](basic-information/#endpoint-security-type)

Endpoints under **Trade** require an [API-key and a signature.](basic-information/#signed-trade-and-user_data-endpoint-security)

#### New Order

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/margin/order**</font>

Rate Limit: **100times/2s**

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
volume | number | Order vol. For ```MARKET BUY``` orders, vol=amount.
side | string |  Side of the order, ```BUY/SELL```
type | string | Type of the order, ```LIMIT/MARKET```
price | number | Order price, ```REQUIRED``` for ```LIMIT``` orders
newClientOrderId | string | Unique order ID generated by users to mark their orders
recvWindow | string | Time window

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The leverage order was sent successfully

==-

#### Query Order

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/margin/order**</font>

Rate Limit: **20times/2s**

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
orderId | string | Order ID
newClientOrderId | string |  Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

#### Cancel Order

==- [!button corners="pill" size="xs" text="POST" variant="success"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/margin/cancel**</font>

Rate Limit: **100times/2s**

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
orderId | string | Order ID
newClientOrderId | string |  Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444

---

**Responses**

🟢 &nbsp; &nbsp; 200 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The leverage order was successfully canceled.

==-

#### Current Open Orders

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/margin/openOrders**</font>

Rate Limit: **20times/2s**

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
limit | string | Default 100; Max 1000

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-

#### Trades

==- [!button corners="pill" size="xs" text="GET"] <font size="2"><span style="color:#8899A8">https://openapi.bitstan.trade</span>**/sapi/v1/margin/myTrades**</font>

Rate Limit: **20times/2s**

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
limit | string | Default 100; Max 1000
limit | integer | Trade Id to fetch from

---

**Responses**

🟢 &nbsp; &nbsp; 200

==-