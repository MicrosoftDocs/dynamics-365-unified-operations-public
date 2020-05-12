## Currencies to transactioncurrencies

This template synchronizes data between Finance and Operations apps and Common Data Service.

Source filter: ((CURRENCYCODE != "999"))

Finance and Operations field | Map type | Other Dynamics 365 field | Default value
---|---|---|---
CURRENCYCODE | = | isocurrencycode | 
NAME | = | currencyname | 
SYMBOL | = | currencysymbol | 
none | >> | exchangerate | 1
