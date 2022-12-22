---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

This is API documentation for second homework

# Authentication

> To authorize, use this code:

```ruby
require 'cards'

api = Cards::APIClient.authorize!('meowmeowmeow')
```


```shell
# With shell, you can just pass the correct header with each request
curl "http::/localhost:8000" \
  -H "Authorization:Bearer meowmeowmeow"
```

```javascript
const axios = require('axios');

axios.defaults.headers.common['Authorization'] = 'Bearer meowmeowmeow';
```

> Make sure to replace `meowmeowmeow` with your API key.

To access certain endpoints, you will need an API key. You can get the API key either by registering a new account or logging into your current account

`Authorization: Bearer meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Cards

## Get All Cards

```ruby
require 'cards'

api = Cards::APIClient
api.cards.get
```

```shell
curl "http://localhost:8000/api/cards" \
  -H "Authorization:Bearer meowmeowmeow"
```

```javascript
const axios = require('axios');

axios.defaults.headers.common['Authorization'] = 'Bearer meowmeowmeow';
let cards = axios.get('http://localhost:8000/api/cards')
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "cardNumber": "93203299339",
    "expirationDate": "2023-04-02",
    "account": {
      "id":1,
      "accountNumber":"1234153245234522",
      "balance":4923432
    },
    "manufacturer":{
      "id":1,
      "legalName":"Visa LLD",
      "name":"VISA",
      "location":"New York"
    }
  },
  {
    "id": 2,
    "cardNumber": "325253235",
    "expirationDate": "2023-05-02",
     "account": {
      "id":2,
      "accountNumber":"1234768234522",
      "balance":338807
    },
    "manufacturer":{
      "id":2,
      "legalName":"MasterCard LLD",
      "name":"MasterCard",
      "location":"New York"
    }
  }
]
```

This endpoint retrieves all cards.

### HTTP Request

`GET http://localhost:8000/api/cards`

## Get a Specific Card

```ruby
require 'cards'

api = Cards::APIClient
api.cards.get(1)
```

```shell
curl "http://localhost:8000/api/cards/1" \
  -H "Authorization:Bearer meowmeowmeow"
```

```javascript
const axios = require('axios');

axios.defaults.headers.common['Authorization'] = 'Bearer meowmeowmeow';
let card = axios.get('http://localhost:8000/api/cards/1')
```

> The above command returns JSON structured like this:

```json
 {
    "id": 1,
    "cardNumber": "93203299339",
    "expirationDate": "2023-04-02",
    "account": {
      "id":1,
      "accountNumber":"1234153245234522",
      "balance":4923432
    },
    "manufacturer":{
      "id":1,
      "legalName":"Visa LLD",
      "name":"VISA",
      "location":"New York"
    }
  }
```

This endpoint retrieves a specific card.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://localhost:8000/api/cards/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the card to retrieve


## Create new Card

```ruby
require 'cards'

api = Cards::APIClient.authorize!('meowmeowmeow')
api.cards.create({
  "card_number": "13413153",
  "expiration_date": "2023-04-02",
  "account_id":2,
  "manufacturer_id" :1
})
```

```shell
curl "http://example.com/api/cards" \
  -X POST \
  -H "Authorization:Bearer meowmeowmeow"

  "{
  \"card_number\": \"13413153\",
  \"expiration_date\": \"2023-04-02\",
  \"account_id\":1,
  \"manufacturer_id\" :1
}"
```

```javascript
const axios = require('axios');

axios.defaults.headers.common['Authorization'] = 'Bearer meowmeowmeow';
axios.post('http://localhost:8000/api/cards',{
  "card_number": "13413153",
  "expiration_date": "2023-04-02",
  "account_id":2,
  "manufacturer_id" :1
})
```


> The above command returns JSON structured like this:

```json
 {
    "id": 3,
    "cardNumber": "13413153",
    "expirationDate": "2023-04-02",
    "account": {
      "id":1,
      "accountNumber":"1234153245234522",
      "balance":4923432
    },
    "manufacturer":{
      "id":1,
      "legalName":"Visa LLD",
      "name":"VISA",
      "location":"New York"
    }
  }
```



This endpoint deletes a specific card.

### HTTP Request

`POST http://localhost:8000/api/cards`

### Requst body

Parameter         | Type        
---------------   | ----------- 
card_number       | String      
expiration_date   | Date     
account_id        | Integer     
manufacturer_id   | Integer     


## Create update Card

```ruby
require 'cards'

api = Cards::APIClient.authorize!('meowmeowmeow')
api.cards.update(3,{
  "card_number": "13413153",
  "expiration_date": "2023-04-02",
  "account_id":2,
  "manufacturer_id" :1
})
```

```shell
curl "http://example.com/api/cards/3" \
  -X PUT \
  -H "Authorization:Bearer meowmeowmeow"

  "{
  \"card_number\": \"13413153\",
  \"expiration_date\": \"2023-04-02\",
  \"account_id\":1,
  \"manufacturer_id\" :1
}"
```

```javascript
const axios = require('axios');

axios.defaults.headers.common['Authorization'] = 'Bearer meowmeowmeow';
axios.post('http://localhost:8000/api/cards/3',{
  "card_number": "13413153",
  "expiration_date": "2023-04-02",
  "account_id":2,
  "manufacturer_id" :1
})
```


> The above command returns JSON structured like this:

```json
 {
    "id": 3,
    "cardNumber": "13413153",
    "expirationDate": "2023-04-02",
    "account": {
      "id":1,
      "accountNumber":"1234153245234522",
      "balance":4923432
    },
    "manufacturer":{
      "id":1,
      "legalName":"Visa LLD",
      "name":"VISA",
      "location":"New York"
    }
  }
```



This endpoint deletes a specific card.

### HTTP Request

`PUT http://localhost:8000/api/cards/3`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the card to delete


### Requst body

Parameter         | Type        
---------------   | ----------- 
card_number       | String      
expiration_date   | Date     
account_id        | Integer     
manufacturer_id   | Integer     



## Delete a Specific Card

```ruby
require 'cards'

api = Cards::APIClient.authorize!('meowmeowmeow')
api.cards.delete(1)
```

```shell
curl "http://example.com/api/cards/1" \
  -X DELETE \
  -H "Authorization:Bearer meowmeowmeow"
```

```javascript
const axios = require('axios');

axios.defaults.headers.common['Authorization'] = 'Bearer meowmeowmeow';
axios.delete('http://localhost:8000/api/cards/1')
```


> The above command returns no response



This endpoint deletes a specific card.

### HTTP Request

`DELETE http://localhost:8000/api/cards/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the card to delete

