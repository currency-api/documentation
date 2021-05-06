---
lang: en-US
title: Quick Start Guide 🚀
description: Currency API
---

# Introduction

Currency API is fast and friendly crypto, commodity, and FX Currency Conversion JSON API, covering over 1200+ pairs.

## Requirements

We've made it easy to be up and running. All you need to do is to visit "My Account" and locate your token. If you don't have one yet, please subscribe and get one immediately.

## Getting Started

Get ready to connect to Currency API using few coding lines of your favorite programming language.

### Definitions

| Definition       | Description                                                                                          |
| ---------------- | ---------------------------------------------------------------------------------------------------- |
| API URL          | The URL which all API request endpoints and URLs are based on.                                       |
| Token            | The access key assigned to your account and used to authenticate with the API.                       |
| Symbol           | The three-letter currency code or currency pair (e.g., EUR, EURUSD).                                 |
| Base Currency    | The currency to which exchange rates are relative to. (If 1 USD = X EUR, USD is the base currency)   |
| Target Currency  | The currency an amount is converted to. (If 1 USD = X EUR, EUR is the target currency)               |
| Timestamp format | All timestamps are unix/epoch timestamps (seconds that have passed since since January 1, 1970 UTC). |

### API URL

The Currency API comes with a single endpoint that enables you to query one or many currency codes or pairs, with readable parameters.
Depending on your subscription plan, the endpoint will return real-time exchange rate data.

```md:no-line-numbers
https://api.currencyapi.io/
```

### Authentication (Token)

Your API token is a unique access key passed into the API URL's token parameter to authenticate with the Currency API. The following is an example of how to append the access token for authentication:

```js:no-line-numbers
https://api.currencyapi.io/markets
    ?token=ACCESS_TOKEN
```

### Available symbols (Pairs)

To get the complete list of a specific market (e.g., Forex, Crypto, etc.) available symbols/pairs, use the following endpoint. Replace the `MARKET_NAME` with the targeted market (crypto or forex)

```js:no-line-numbers
https://api.currencyapi.io/markets
    ?token=ACCESS_TOKEN
    &market=MARKET_NAME
```

### REST API Calls

`/markets` endpoint provides you the ability to query a base currency (e.g., EUR) or currency pair (e.g.,EURUSD).

#### Query with base curency

```js:no-line-numbers
GET https://api.currencyapi.io/markets
    ?token=ACCESS_TOKEN
    &symbol=SYMBOL
```

#### Response

```json:no-line-numbers
[
 {
  "t":"2021-04-15T03:53:00.593Z",
  "tms":"1618458780086",
  "s":"EURUSD",
  "b":1.19864,
  "bd":0,
  "a":1.19867,
  "ad":1,
  "p":5
 }
]
```

### Response JSON Structure

| Key | Description                                                                                                   |
| --- | ------------------------------------------------------------------------------------------------------------- |
| t   | The last update date/time of query result.                                                                    |
| tms | The last update timestamp of query result.                                                                    |
| s   | The currency pair.                                                                                            |
| b   | The bid price. It is also referring to the highest price a buyer will pay for a currency.                     |
| bd  | The bid price direction. It is also referring to the color code of the displayed bid price (e.g., red/green). |
| a   | The ask price. It is also referring to the lowest price a seller will accept for a currency.                  |
| ad  | The ask price direction. It is also referring to the color code of the displayed ask price (e.g., red/green). |
| p   | The Currency precision                                                                                        |

## Code Examples

Currency API supports your favorite programming languages. Here are few examples of how to connect and start getting real-time quotes:

### JavaScript

<CodeGroup>
  <CodeGroupItem title="Fetch">

```js
var requestOptions = {
  method: 'GET',
  redirect: 'follow'
};

fetch(
 "https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL",
 requestOptions
 )
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

  </CodeGroupItem>

  <CodeGroupItem title="JQuery">

```js
var settings = {
  "url": "https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL",
  "method": "GET",
  "timeout": 0,
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

  </CodeGroupItem>

 <CodeGroupItem title="XHR">

```js
var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL");

xhr.send();
```

  </CodeGroupItem>
</CodeGroup>

### PHP

<CodeGroup>
 <CodeGroupItem title="cURL">

```php
var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open(
 "GET",
 "https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL"
);

xhr.send();
```

 </CodeGroupItem>

 <CodeGroupItem title="HTTP_Request2">

```php
<?php
require_once 'HTTP/Request2.php';
$request = new HTTP_Request2();
$request->setUrl(
 'https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL'
);
$request->setMethod(HTTP_Request2::METHOD_GET);
$request->setConfig(array(
  'follow_redirects' => TRUE
));
try {
  $response = $request->send();
  if ($response->getStatus() == 200) {
    echo $response->getBody();
  }
  else {
    echo 'Unexpected HTTP status: ' . $response->getStatus() . ' ' .
    $response->getReasonPhrase();
  }
}
catch(HTTP_Request2_Exception $e) {
  echo 'Error: ' . $e->getMessage();
}
```

 </CodeGroupItem>

<CodeGroupItem title="pecl_http">

```php
<?php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl(
 'https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL'
);
$request->setRequestMethod('GET');
$request->setOptions(array());

$client->enqueue($request)->send();
$response = $client->getResponse();
echo $response->getBody();
```

 </CodeGroupItem>

</CodeGroup>

### Python

<CodeGroup>
 <CodeGroupItem title="http.client">

```py
import http.client

conn = http.client.HTTPSConnection("api.currencyapi.io")
conn.request(
 "GET",
 "/markets?token=ACCESS_TOKEN&symbol=SYMBOL",
)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

 </CodeGroupItem>

 <CodeGroupItem title="Requests">

```py
import requests

url = "https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

 </CodeGroupItem>

</CodeGroup>

### PowerShell

<CodeGroup>
 <CodeGroupItem title="RestMethod">

```powershell
$response = Invoke-RestMethod 'https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL' -Method 'GET' -Headers $headers
$response | ConvertTo-Json
```

 </CodeGroupItem>

</CodeGroup>

### cURL

<CodeGroup>
 <CodeGroupItem title="curl">

```md:no-line-numbers
curl --location --request GET 'https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL'
```

 </CodeGroupItem>

</CodeGroup>

### C#

<CodeGroup>
 <CodeGroupItem title="RestSharp">

```objectivec
var client = new RestClient("https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

 </CodeGroupItem>

</CodeGroup>

### Go (Native)

<CodeGroup>
 <CodeGroupItem title="Native">

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL"
  method := "GET"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

 </CodeGroupItem>

</CodeGroup>

### Ruby

<CodeGroup>
 <CodeGroupItem title="Net::HTTP">

```ruby
require "uri"
require "net/http"

url = URI("https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Get.new(url)

response = https.request(request)
puts response.read_body
```

 </CodeGroupItem>

</CodeGroup>

### Swift

<CodeGroup>
 <CodeGroupItem title="URLSession">

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

var request = URLRequest(url: URL(
 string: "https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL")!,
 timeoutInterval: Double.infinity
)
request.httpMethod = "GET"

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

 </CodeGroupItem>

</CodeGroup>

### NodeJs

<CodeGroup>
 <CodeGroupItem title="Axios">

```js
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL',
  headers: { }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```

 </CodeGroupItem>

 <CodeGroupItem title="Request">

```js
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL',
  'headers': {
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```

 </CodeGroupItem>
</CodeGroup>

### Java

<CodeGroup>
 <CodeGroupItem title="OkHttp">

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL")
  .method("GET", null)
  .build();
Response response = client.newCall(request).execute();
```

 </CodeGroupItem>
 <CodeGroupItem title="Unirest">

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.get("https://api.currencyapi.io/markets?token=ACCESS_TOKEN&symbol=SYMBOL")
  .asString();
```

 </CodeGroupItem>
</CodeGroup>
