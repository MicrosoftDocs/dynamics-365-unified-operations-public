## Exchange rate currency pair to msdyn_currencyexchangeratepairs

This template synchronizes data between Finance and Operations and Common Data Service.

Source field | Map type | Destination field
---|---|---
EXCHANGERATETYPENAME | = | msdyn_exchangeratetypetext
FROMCURRENCYCODE | = | msdyn_fromtransactioncurrencyidtext
TOCURRENCYCODE | = | msdyn_totransactioncurrencyidtext
EXCHANGERATEDISPLAYFACTOR | >< | msdyn_displayfactor
EXCHANGERATETYPENAME | = | msdyn_currencyexchangeratetypeid.msdyn_name
FROMCURRENCYCODE | = | msdyn_fromtransactioncurrencyid.isocurrencycode
TOCURRENCYCODE | = | msdyn_totransactioncurrencyid.isocurrencycode
