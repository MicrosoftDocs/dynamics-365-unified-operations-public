## Exchange rate currency pair to msdyn_currencyexchangeratepairs

This template synchronizes data between Finance and Operations apps and Common Data Service.

Finance and Operations field | Map type | Other Dynamics 365 field | Default value
---|---|---|---
EXCHANGERATETYPENAME | = | msdyn_exchangeratetypetext | 
FROMCURRENCYCODE | = | msdyn_fromtransactioncurrencyidtext | 
TOCURRENCYCODE | = | msdyn_totransactioncurrencyidtext | 
EXCHANGERATEDISPLAYFACTOR | >< | msdyn_displayfactor | 
EXCHANGERATETYPENAME | = | msdyn_currencyexchangeratetypeid.msdyn_name | 
FROMCURRENCYCODE | = | msdyn_fromtransactioncurrencyid.isocurrencycode | 
TOCURRENCYCODE | = | msdyn_totransactioncurrencyid.isocurrencycode | 
