## Ledger to msdyn_ledgers

This template synchronizes data between Finance and Operations apps and Common Data Service.

Finance and Operations field | Map type | Other Dynamics 365 field | Default value
---|---|---|---
LEGALENTITYID | >> | msdyn_company.cdm_companycode | 
DESCRIPTION | >> | msdyn_description | 
ACCOUNTINGCURRENCY | >> | msdyn_accountingcurrency.isocurrencycode | 
ISBUDGETCONTROLENABLED | >> | msdyn_isbudgetcontrolenabled | 
NAME | >> | msdyn_name | 
REPORTINGCURRENCY | >> | msdyn_reportingcurrency.isocurrencycode | 
BUDGETEXCHANGERATETYPE | >> | msdyn_budgetexchangeratetype.msdyn_name | 
CHARTOFACCOUNTS | >> | msdyn_chartofaccounts.msdyn_name | 
EXCHANGERATETYPE | >> | msdyn_exchangeratetype.msdyn_name | 
FISCALCALENDAR | >> | msdyn_fiscalcalendar.msdyn_calendar | 
REPORTINGCURRENCYEXCHANGERATETYPE | >> | msdyn_reportingcurrencyexchangeratetype.msdyn_name | 
