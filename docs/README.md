# Introduction

Currency API is fast and friendly crypto, commodity, and FX Currency Conversion JSON API, covering over 1200+ pairs.

## Requirements

We've made it easy to be up and running. All you need to do is to visit "My Account" and locate your token. If you don't have one yet, please subscribe and get one immediately.

## Quick Start Guide 🚀

Get ready to connect to Currency API using few coding lines of your favorite programming language.

### Definitions

| Definition | Description  |
|---|---|
| API URL  |  The URL which all API request endpoints and URLs are based on. |
| Token  | The access key assigned to your account and used to authenticate with the API. |
| Symbol  | The three-letter currency code or currency pair (e.g., EUR, EURUSD).  |
| Base Currency  | The currency to which exchange rates are relative to. (If 1 USD = X EUR, USD is the base currency) |
| Target Currency  | The currency an amount is converted to. (If 1 USD = X EUR, EUR is the target currency)  |

### API URL

The Currency API comes with a single endpoint that enables you to query one or many currency codes or pairs, with readable parameters.
Depending on your subscription plan, the endpoint will return real-time exchange rate data.

```md:no-line-numbers
https://api.currencyapi.io/
```

### Authentication (Token)

Your API token is a unique access key passed into the API URL's token parameter to authenticate with the Currency API. The following is an example of how to append the access token to authenticate:

```js:no-line-numbers
https://api.currencyapi.io/markets?token=ACCESS_TOKEN
```

