<a name="Webhook"></a>

## Webhook
Top.gg Webhook

**Kind**: global class  

* [Webhook](#Webhook)
    * [new Webhook(authorization)](#new_Webhook_new)
    * [.middleware()](#Webhook+middleware)

<a name="new_Webhook_new"></a>

### new Webhook(authorization)
Create a new webhook client instance


| Param | Description |
| --- | --- |
| authorization | Webhook authorization to verify requests |

**Example**  
```js
const express = require('express')
const { Webhook } = require(`@top-gg/sdk`)

const app = express()
const wh = new Webhook('webhookauth123')

app.post('/dblwebhook', wh.middleware(), (req, res) => {
  // req.vote is your vote object e.g
  console.log(req.vote.user) // => 321714991050784770
})

app.listen(80)

// In this situation, your TopGG Webhook dashboard should look like
// URL = http://your.server.ip:80/dblwebhook
// Authorization: webhookauth123
```
<a name="Webhook+middleware"></a>

### webhook.middleware()
Middleware function to pass to express, sets req.vote to the payload

**Kind**: instance method of [<code>Webhook</code>](#Webhook)  
**Example**  
```js
app.post('/dblwebhook', wh.middleware(), (req, res) => {
  // req.vote is your payload e.g
  console.log(req.vote.user) // => 395526710101278721
})
```
