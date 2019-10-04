## Withholding tax codes to msdyn_withholdingtaxcodes

This template synchronizes data between Finance and Operations and Common Data Service.

Source field | Map type | Destination field
---|---|---
WITHHOLDINGCODE | = | msdyn_name
WITHHOLDINGTAXNAME | = | msdyn_description
WITHHOLDINGTAXROUNDOFF | = | msdyn_roundoff
WITHHOLDINGTAXROUNDOFFTYPE | >< | msdyn_roundofftype
CURRENCYCODEID | = | msdyn_currency.isocurrencycode
WITHHOLDINGTAXBASE | >< | msdyn_taxableamountorigin
