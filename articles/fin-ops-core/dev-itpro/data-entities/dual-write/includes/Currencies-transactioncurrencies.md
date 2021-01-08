## Currencies to transactioncurrencies

This template synchronizes data between Finance and Operations apps and Dataverse.

Source filter: `((CURRENCYCODE != "999"))`

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
CURRENCYCODE | = | isocurrencycode | 
NAME | = | currencyname | 
SYMBOL | = | currencysymbol | 
none | >> | exchangerate | 1
